package com.example.abd_elrhman.abdotgmi3;


import android.os.Bundle;
import android.support.v4.app.Fragment;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.Toast;


/**
 * A simple {@link Fragment} subclass.
 */
public class Events extends Fragment implements Afterfinish.ExitInterface {


    public Events() {
        // Required empty public constructor
    }
    @Override
    public void onBackPressed() {
        Toast.makeText(getContext(), "Please press Back again to exit", Toast.LENGTH_SHORT).show();
    }


    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        return inflater.inflate(R.layout.fragment_events, container, false);
    }

}
