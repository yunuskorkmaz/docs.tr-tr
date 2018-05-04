### <a name="wpf-pointer-based-touch-stack"></a>WPF işaretçi tabanlı dokunma yığını

|   |   |
|---|---|
|Ayrıntılar|Bu değişiklik, isteğe bağlı bir WM_POINTER etkinleştirme özelliği WPF dokunma/kalem yığın tabanlı ekler.  Bu açıkça olarak etkinleştirmeyin geliştiriciler WPF dokunma/kalem davranışında değişiklik görmeniz gerekir. Geçerli bilinen sorunlar ile isteğe bağlı WM_POINTER dokunma/kalem yığını temel:<ul><li>Gerçek zamanlı mürekkep desteği yoktur.</li><li>Mürekkep sırasında ve StylusPlugIns çalışmaya, UI sağlamakta performansın için iş parçacığı üzerinde işlenir.</li><li>Fare olayları dokunma/kalem olaylardan yükseltmesine değişiklikleri nedeniyle davranış değişiklikleri</li><li>İşleme farklı davranabilir</li><li>Sürükle ve bırak dokunma girişi için uygun bildirim gösterme</li><li>Bu kalem giriş etkilemez</li><li>Sürükle ve bırak artık dokunma/kalem olaylarına başlatılabilir</li><li>Fare girişi algılandığında kadar bu uygulama potansiyel olarak askıda kalabilir.</li><li>Bunun yerine, geliştiricilerin Sürükle başlatmak ve bu fare olayları bırakma gerekir.</li></ul>|
|Öneri|Bu yığın etkinleştirmek istediğiniz geliştiriciler ekleme/kendi uygulamanın App.config dosyasını aşağıdaki birleştirme:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Bu kaldırarak veya değeri false olarak ayarlayarak bu isteğe bağlı yığını kapanır. Bu yığına yalnızca Windows 10 oluşturucuları güncelleştirme veya sonraki kullanılabilir olduğunu unutmayın.|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Yeniden hedefleme|

