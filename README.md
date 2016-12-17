package com.example.andriod.database_project_ui2;


import android.content.DialogInterface;
import android.os.Bundle;
import android.support.v4.app.Fragment;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.AdapterView;
import android.widget.ArrayAdapter;
import android.widget.ListView;
import android.widget.TabHost;
import android.widget.Toast;

/**
 * A simple {@link Fragment} subclass.
 */
 // feryal : kan fady copy kolo
public class Events extends Fragment {


    public Events() {
        // Required empty public constructor
    }

    ListView mListView;
    TabHost chooseDon;
    //FragmentManager fm = Fragment.getFragmentManager();
    String[] data_for_financial = {
            "Amount needed in L.E: \nPeriod: \nDisabled Contact",
            "Amount needed in L.E: \nPeriod: \nDisabled Contact",
            "Amount needed in L.E: \nPeriod: \nDisabled Contact",
            "Amount needed in L.E: \nPeriod: \nDisabled Contact",
            "Amount needed in L.E: \nPeriod: \nDisabled Contact",
            "Amount needed in L.E: \nPeriod: \nDisabled Contact",
            "Amount needed in L.E: \nPeriod: \nDisabled Contact",


    };

    String[] data_for_material = {
            "Type : \nDisabled Contact",
            "Type : \nDisabled Contact",
            "Type : \nDisabled Contact",
            "Type : \nDisabled Contact",
            "Type : \nDisabled Contact",
            "Type : \nDisabled Contact",
    };
    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        View rootView= inflater.inflate(R.layout.fragment_events, container, false);

        chooseDon = (TabHost) rootView.findViewById(R.id.Home_events);
        chooseDon.setup();


        TabHost.TabSpec spec1 = chooseDon.newTabSpec("Tab One");
        spec1.setContent(R.id.attend_events_tab);
        spec1.setIndicator("Your Events");
        chooseDon.addTab(spec1);


        //Tab 2
        TabHost.TabSpec spec2 = chooseDon.newTabSpec("Tab Two");
        spec2.setContent(R.id.events_tab);
        spec2.setIndicator("Events");
        chooseDon.addTab(spec2);

        mListView = (ListView) rootView.findViewById(R.id.list_attend_events);
        mListView.setAdapter(new ArrayAdapter<String>(getActivity(),
               android.R.layout.simple_list_item_1, data_for_financial));
        mListView.setChoiceMode(ListView.CHOICE_MODE_SINGLE);
        mListView.setOnItemClickListener(new AdapterView.OnItemClickListener() {
            public void onItemClick(AdapterView<?> myAdapter, View myView, int myItemInt, long mylng) {
                String selectedFromList = (String) (mListView.getItemAtPosition(myItemInt));
                //Toast.makeText(getActivity(), selectedFromList, Toast.LENGTH_LONG).show();
                //AlertDialog
                displayDialog("Do you want to remove this event from your events?","Event Removed",
                        "");

            }
        });
        mListView = (ListView)  rootView.findViewById(R.id.list_general_events);
        mListView.setAdapter(new ArrayAdapter<String>(getActivity(),
                android.R.layout.simple_list_item_1, data_for_material));
        mListView.setChoiceMode(ListView.CHOICE_MODE_SINGLE);
        mListView.setOnItemClickListener(new AdapterView.OnItemClickListener() {
            public void onItemClick(AdapterView<?> myAdapter, View myView, int myItemInt, long mylng) {
                String selectedFromList = (String) (mListView.getItemAtPosition(myItemInt));
                //Toast.makeText(getActivity(), selectedFromList, Toast.LENGTH_LONG).show();

                //AlertDialog
                displayDialog("Do you want to attend this event?","Event is saved to your events",
                        "");

            }
        });
        return rootView;
    }

    public void displayDialog (String Mes, final String YesMes, final String NoMes)
    {
        android.app.AlertDialog.Builder builder = new android.app.AlertDialog.Builder(getActivity());
        builder.setMessage(Mes);
        builder.setTitle("Choose Action");
        builder.setPositiveButton("YES", new DialogInterface.OnClickListener() {
            public void onClick(DialogInterface dialog, int id) {
                Toast.makeText(getActivity(),YesMes,Toast.LENGTH_LONG).show();
            }
        });
        builder.setNegativeButton("NO", new DialogInterface.OnClickListener() {
            public void onClick(DialogInterface dialog, int id) {
                if(!NoMes.equals(""))
                Toast.makeText(getActivity(),NoMes,Toast.LENGTH_LONG).show();

            }
        });
        //Instantiate an AlertDialog.Builder with its constructor
        //AlertDialog.Builder builder = new AlertDialog.Builder(getActivity());
        //Get the AlertDialog from create()
        android.app.AlertDialog dialog = builder.create();
        dialog.show();
    }
}
