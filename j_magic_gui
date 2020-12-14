import PySimpleGUI as sg
import traceback
import time

def gui():

    sg.theme('DarkGrey13')
   
    layout = [
        [sg.Text('Operation REAS Witherspoon')],
        [sg.Text('Bucket Name', size =(60, 1), ),  sg.InputText('clgx-surveillance-sbx-analysts')], 
        [sg.Text('File Path',  size =(60, 1)), sg.InputText()], 
        [sg.Text('GCS Path and File Name', size =(60, 1)), sg.InputText()], 
        [sg.Text('Google Service Key Path',  size =(60, 1)), sg.InputText()], 
        
        [sg.Submit('J Magic'), sg.Cancel('Cancel')] ,
    ]

    window = sg.Window('Upload Files Directly to GCS', layout)
        
    event, values = window.read()
    window.close()
    bucket = str(values[0])
    file_path = str(values[1])
    gcs_path = str(values[2])
    service_key_path = str(values[3])

    if event ==('J Magic'):
        
        try:
            
            upload_blob(service_key_path, bucket, file_path, gcs_path)

            sg.theme('DarkGrey11')
            layout = [
                [sg.Text(file_path + ' uploaded to ' + bucket + 
                         '. This file can be found under the GCS path: '+
                        gcs_path)],
                [sg.Cancel('Ok')] ,
                        ]
            window = sg.Window('Finished Uploading', layout)
            event, values = window.read()

            # loop that would normally do something useful

            window.close()     
        except Exception as e:
            error_message = str(e)
            traceback_message = traceback.format_exc()
            layout = [
                [sg.Text("""Something went wrong! \n
Error Message: \n
{}
Traceback: \n
{}""".format(error_message, traceback_message))], 
                [sg.Cancel('Exit')],   
            ]
            
            window = sg.Window('Oh no! I encountered an error :-(', layout)
            event, values = window.read()
            if event == ('Exit'):
                window.close()
    return None      

if __name__ == "__main__": 
    gui()
