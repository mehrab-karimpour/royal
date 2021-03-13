https://www.bycheck.ir/Credit/Order/ghesticlub


import React, {useState} from 'react';
import '../styles/dependencies/HourMinuteSelect.scss';


const HourSelectComponent = () => {
    const [hour, setHour] = useState("08");
    const [minute, setMinute] = useState("00");


    function arrowsHandler(dateType, arrowDirection) {
        switch (dateType) {
            case 'hour':
                switch (arrowDirection) {
                    case 'top':
                        if ((parseInt(hour) / 2) < 4) {
                            setHour('');
                            setHour(`0${parseInt(hour) + 1}`);
                        } else if (parseInt(hour) === 8) {
                            setHour(`0${parseInt(hour) + 1}`);
                        } else if (parseInt(hour) === 24) {
                            setHour('');
                            setHour("0" + 0);
                        } else {
                            setHour('');
                            setHour(parseInt(hour) + 1);
                        }
                        break
                    case 'bottom':

                        if ((parseInt(hour) / 2) <= 5) {
                            if (parseInt(hour) === 0) {
                                setHour('');
                                setHour(24);
                            } else {
                                setHour('');
                                setHour(`0${parseInt(hour) - 1}`);
                            }
                        } else if (parseInt(hour) === 8) {
                            setHour(`0${parseInt(hour) - 1}`);
                        } else {
                            setHour('');
                            setHour(parseInt(hour) - 1);
                        }
                }
                break
            case 'minute':
                switch (arrowDirection) {
                    case 'top':
                        if (parseInt(minute) > 60) {
                            setMinute(0);
                        } else {
                            setMinute(parseInt(minute + 1))
                        }
                        break
                    case 'bottom':

                        if (parseInt(minute) < 1) {
                            setMinute(60);
                        } else {
                            setMinute(parseInt(minute) - 1)
                        }
                }
        }
    }

    return (
        <main className="p-0">
            <section id="hour-select">

                <div id="arrow-top" className="d-flex justify-content-around align-items-center">
                    <div
                        onClick={() => {
                            arrowsHandler('minute', 'top');
                        }}
                        className='arrow-top-change-minute'>
                        &uarr;
                    </div>
                    <div
                        onClick={() => {
                            arrowsHandler('hour', 'top');
                        }}
                        className="arrow-top-change-hour">
                        &#x2191;
                    </div>
                </div>

                <div id="show-hour" className="d-flex justify-content-around align-items-center">
                    <input
                        className="hour-show"
                        type="number"
                        name="hour"
                        onChange={(e) => {
                            setMinute(e.target.value);
                        }}
                        value={minute}
                    />
                    <input
                        className="hour-show"
                        type="number"
                        name="hour"
                        onChange={(e) => {
                            setHour(e.target.value)
                        }}
                        value={hour}
                    />
                </div>

                <div id="arrow-bottom" className="d-flex justify-content-around align-items-center">
                    <div
                        onClick={() => {
                            arrowsHandler('minute', 'bottom');
                        }}
                        className='arrow-bottom-change-minute'>
                        &#8595;
                    </div>
                    <div
                        onClick={() => {
                            arrowsHandler('hour', 'bottom');
                        }}
                        className="arrow-bottom-change-hour">
                        &#8595;
                    </div>
                </div>
            </section>
        </main>
    );
}

export default HourSelectComponent;

