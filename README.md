@extends('layouts.master')

@section('head')
@include('templates.dldready-sneaky-purple-spa.style')
    <style>
    body {
      background: white;
      display: flex;
      flex-direction: column;
      min-height: 100vh;
    }
.cstm_footer_link{display:none1}
    .main_cntnt{
            width: 100%;
            overflow-x: hidden;
            padding: 4px;
            margin: 0 auto;
            position: relative;
            background-repeat: no-repeat;
            -webkit-background-position: top;
            background-position: top;
            -webkit-background-size: contain;
            background-size: contain;
    }
.white_img{
  width: 10rem;
  
}
.bor{
  border-radius: 10px;
}

  </style>
@endsection

@section('content')
<div class="main_cntnt ">
          <p class="font-base text-xs text-stone-400 text-center">{{t('Free for 24 hours then AED 3.25 / day (VAT INCLUSIVE)')}}</p>
<div class="flex items-center justify-center w-full p-4 ">
    <div class="w-96">
          <div class="grid grid-cols-3">
            <div class="py-6">
                 @include('components.menu', ['menuButtonColor' => 'black', 'navItems' => ['All Content' => $campaign->getTemplateConfig('menu_link', request()->getSchemeAndHttpHost())]])
            </div>
            <div class="p-2 flex justify-center">
                 <img src="{{ asset('assets/images/templates/fitup/fitup7_logo.png');}}" style="width: 4rem;filter: grayscale(1);" alt="">
            </div>

            <div class="px-3 grid justify-items-end place-items-center">
                @include('components.language_change')
            </div>
        </div>

   <div class="mt-1">
                <div class="text-center">
                    <p class="font-base text-l text-center step_2_hide">{{t('CONTINUE TO GET')}}</p>
                    <p id="phone_otp_text" class="font-extrabold text-xl"></p>
                </div>
                <div class="text-center mt-2 italic step_2_hide">
                    <p class="font-bold text-xl text-center"> <span style="border-radius: 3PX;" class="bg-blue-500 text-white p-1 mr-1 text-center"> {{t('access')}} </span> <span class="{{ app()->getLocale() == 'en' ? '' : 'mr-3'}}"> {{t('to your VIP subscription')}} </span></p>
                </div>

            <div class="w-full mt-2 text-center">
                <div id="annoying-notification" style="display: none; width: 358px;" class="absolute mt-4 z-10 bg-red-400 text-white font-bold animate-bounce">
                    {{ t('') }}
                </div>
                <div class="grid grid-cols-1">
                      <div class="p-2 flex justify-center">
                         <img id="send_otp_img" class="text-bold" src="{{ asset('assets/images/templates/fitup/check.svg');}}" style="width: 4rem;" alt="">
                          <img id="verify_otp_img" class="hidden h-28" src="{{ asset('assets/images/templates/black_white_two_download_arrow_blue.png');}}"  alt="">
                      </div>
                </div>
                 <div class="text-center mt-2 italic">
                      <p class="text-sm text-center hidden"> {{t('The Best Fitness Platform to Train Anywhere!')}}</p>
                  </div>

                <div class="w-90 mt-4" style="    border-radius: 14px; border: solid 0px lightgrey;">
                @livewire('new-subscription-form', [
                    'config' => [
                        'copyrights'  => ['show' => false],
                        'send' => [
                            'top_label' => [
                                'show' => true, 
                                'text'=> 'Enter your UAE Number', 
                                'classes' => ['font-medium',  'text-l' ] 
                              ],
                            'exit' => ['show' => false],
                            'postbutton' => [
                                   'show' => false,
                                    'text' => 'By continuing you are agreeing to be communicated promotional offers',
                                      'classes' => ['text-center', 'text-xs', 'text-stone-400']
                                ],
                            'button' => [
                  
                                'suffix' => ['text' => ''],
                                'text' => 'Subscribe',
                                'classes' => [
                                    'border-2', 'border-white-400', 'w-full', 'rounded-lg', 'py-4', 'px-4', 'font-base', 'text-l', 'text-grey-600', 'mt-5', 'disabled:bg-gray-500', 
                                
                                ],
                                'styles' => ['border-radius: 5px', 'color:white']
                            ],
                            'form' => [
                                'prefix' => [
                                    'show' => true,
                                    'image' => asset('assets/icons/uae_flag.webp'),
                                    'styles' => [''],
                                ],
                                'suffix' => [
                                    'image' => asset('assets/images/shared/check_blue.png'),
                                ],
                                'wrapper' => [
                                    'classes' => [
                                        '@', 'border-2', 'border-white-400', 'p-2', 'flex', 'mt-4', 'rounded-md', 'text-center'
                                    ],
                                    
                                ],
                                'input' => [
                                    'placeholder' => "1 (702) 123-4567",
                                    'top_label' => [
                                        'show' => false,
                                        'styles' => ['background: transparent', 'color:#a8a29e', 'box-shadow: 0px 4px 4px 0px var(--c-shadow) inset;'],
                                    ],
                                    'classes' => [
                                        '@', 'w-full', 'bg-none', 'font-base', 'text-left', 'p-1', 'outline-none bg-transparent' 
                                    ],
                                ]
                            ]
                        ],
                        'verify' => [
                            'exit' => ['show' => false],
                            'button' => [
                                'suffix' => ['text' => ''],
                                'text' => 'Subscribe',
                                'classes' => [
                                    'border-2', 'border-white-400', 'w-full', 'rounded-lg', 'py-4', 'px-4', 'font-base', 'text-l', 'text-grey-600', 'mt-5', 'disabled:bg-gray-300',
                                ],
                                'styles' => ['border-radius: 5px', 'color:white']
                            ],
                            'form' => [
                                'wrapper' => [
                                    'classes' => [
                                        '@', 'border-2', 'border-blue-400', 'p-2', 'flex', 'mt-4', 'rounded-md'
                                    ],
                                ],
                                'input' => [
                                    'top_label' => [
                                        'show' => false,
                                        'text' => 'OTP'
                                    ],
                                    'classes' => [
                                        '@', 'w-full', 'bg-none', 'font-bold', 'text-center', 'p-1', 'outline-none'
                                    ],
                                ]
                            ]
                        ]
                    ],
                ])
               </div>
            </div>
        </div>
    </div>
</div>
    <p class="font-base text-xs text-stone-400 text-center">{{t('Free for 24 hours then AED 3.25 / day (VAT INCLUSIVE)')}}</p>
   <div class="p-1">             
       <div class=" gap-3 text-center text-sm m-3" >
                  <a href="https://www.google.com"  class="inline-block bg-gray-300 text-white mt-3 px-1 text-xs my-5"> {{t('Exit')}} </a>
           </div>
 
      <div class="mt-2 ml-5 text-stone-500 ">
            @include('components.copyrights', ['classes' => 'text-xs text-left'])
        </div>

                    
    <div class="space-y-2 max-w-md mx-auto mt-7 step_2_hide" dir="{{ app()->getLocale() == 'ar' ? 'rtl' : '' }}">
                  
      <details class="group border1 rounded-lg bg-stone-200">
        <summary class="p-1 cursor-pointer list-none flex justify-between items-center bg-stone-400">
          <span class="font-medium ">{{t('What is FitUp7?')}}</span>
          <span class="ml-4 transition-transform group-open:rotate-180 text-2xl font-bold">+</span>
        </summary>
        <div class="mt-3 text-sm text-gray-700 p-1">
          {{t('FitUp7 is a digital fitness platform offering workouts, nutrition tips, and motivational content, allowing you to train anytime, anywhere.')}}
        </div>
      </details>

      <details class="group border1 rounded-lg bg-stone-200">
        <summary class="p-1 cursor-pointer list-none flex justify-between items-center bg-stone-400">
          <span class="font-medium">{{t('What Features Are Included?')}}</span>
          <span class="ml-4 transition-transform group-open:rotate-180 text-2xl font-bold">+</span>
        </summary>
        <div class="mt-3 text-sm text-gray-700 p-1">
          {!!  t('Personalized Workouts – Tailored exercises for your level and goals.<br/><br/>
              
<b>Nutrition Guidance</b>: Tips and meal plans to complement your training.<br/>

<b>Motivational Content</b>: Videos and articles to keep you energized.<br/>

<b>Multi-device Access</b>: Use on mobile phones, tablets, and computers.')
            !!} 
        </div>
      </details>

       <details class="group border1 rounded-lg bg-stone-200">
        <summary class="p-1 cursor-pointer list-none flex justify-between items-center bg-stone-400">
          <span class="font-medium ">{{t('What’s the Cost & How to Cancel?')}}</span>
          <span class="ml-4 transition-transform group-open:rotate-180 text-2xl font-bold">+</span>
        </summary>
        <div class="mt-3 text-sm text-gray-700 p-1">
          {!!  t('<b>Price</b>: After a free 24-hour trial, AED 3.25/day (VAT included).<br/>
<b>Cancel Anytime </b>: Text “C FUP” to 1111 to stop your subscription immediately.<br/>')
            !!} 
        </div>
      </details>

       <details class="group border1 rounded-lg bg-stone-200">
        <summary class="p-1 cursor-pointer list-none flex justify-between items-center bg-stone-400">
          <span class="font-medium ">{{t('Which Devices Are Supported?')}}</span>
          <span class="ml-4 transition-transform group-open:rotate-180 text-2xl font-bold">+</span>
        </summary>
        <div class="mt-3 text-sm text-gray-700 p-1">
          {{t('FitUp7 works on smartphones, tablets, and computers, giving you flexible access anywhere.')}}
        </div>
      </details>

    </div>

  <p class="font-bold text-lg my-6 step_2_hide" dir="{{ app()->getLocale() == 'ar' ? 'rtl' : '' }}">{{t('More Reasons to Join')}}</p>
  <div class="grid grid-cols-2 gap-4 p-4 mt-2 step_2_hide" dir="{{ app()->getLocale() == 'ar' ? 'rtl' : '' }}">
      <div class="bg-stone-200 shadow-md rounded-lg p-1 flex flex-col items-center1">
        <h2 class="font-bold text-sm">{{t('Train Anywhere')}}</h2>
        <p class="text-gray-500 text-sm text-center1">{{t('Access workouts anytime, anywhere.')}}</p>
      </div>
                 
      <div class="bg-stone-200 shadow-md rounded-lg p-1 flex flex-col items-center1">
        <h2 class="font-bold text-sm">{{t('Always Updated')}}</h2>
        <p class="text-gray-500 text-sm text-center1">{{t('New workouts and fitness content every week')}}</p>
      </div>

      <div class="bg-stone-200 shadow-sm rounded-lg p-1 flex flex-col items-center1">
        <h2 class="font-bold text-sm">{{t('No Commitment')}}</h2>
        <p class="text-gray-500 text-sm text-center1">{{t('Cancel whenever you want.')}}</p>
      </div>

      <div class="bg-stone-200 shadow-md rounded-lg p-1 flex flex-col items-center1">
        <h2 class="font-bold text-sm">{{t('Dedicated Support')}}</h2>
        <p class="text-gray-500 text-sm text-center1">{{t('Our team is here to help you succeed.')}}</p>
      </div>

       <div class="bg-stone-200 shadow-md rounded-lg p-1 flex flex-col items-center1">
        <h2 class="font-bold text-sm">{{t('Sports & Energy')}}</h2>
        <p class="text-gray-500 text-sm text-center1">{{t('Get fitness and sports inspiration in one place.')}}</p>
      </div>
       <div class="bg-stone-200 shadow-md rounded-lg p-1 flex flex-col items-center1">
        <h2 class="font-bold text-sm">{{t('Personalized Progress')}}</h2>
        <p class="text-gray-500 text-sm text-center1">{{t('Track your journey and see your improvements every step of the way')}}</p>
      </div>
</div>               
  


    

          
</div>
@endsection

@section('scripts')
<script>
    window.addEventListener("load", () => {
        $(window).on('otp-send-invalid-response-event', (e, resp) => {
            $('#annoying-notification').html("{{ t('Please insert a valid phone number') }}").show();
        });

        $('[data-msisdn-input]').on('change paste keyup input propertychange', (e) => {
            digitsOnly('[data-msisdn-input]');

            $('#annoying-notification').fadeOut();
        });

        msisdnInterval = setInterval(() => {
            let msisdn = $('[data-msisdn-input]').val();

            if (msisdn.length < "{{ $msisdnMinLen }}" || msisdn == "{{ $visit->determineCountryCode() }}") {
                $('#annoying-notification').fadeIn('slow');
            }
        }, 2000);
    });
</script>
@endsection

@section('late_scripts')
<script>
    window.Livewire.on('otp.send.success', () => {
        
         $('.step_2_hide').addClass('hidden');
          $('#verify_otp_img').removeClass('hidden');
          $('#send_otp_img').addClass('hidden');
        $('#phone_otp_text').html("{{ t('Enter The pin Code received') }}");
      goToStep(2);
        clearInterval(msisdnInterval);
  
        otpInterval = setInterval(() => {
            let otp = $('[data-otp-input]').val();

            if (otp.length < "{{ $otpMinLen }}") {
                $('#annoying-notification').html("{{ t('Please insert a valid PIN') }}").fadeIn();
            } else {
                $('#annoying-notification').fadeOut();
            }
        }, 2000);

        $('[data-otp-input]').on('change paste keyup input propertychange', () => {
            digitsOnly('[data-otp-input]');
        });
    });
</script>
@endsection
