---
ms.openlocfilehash: 3463b6c45952aab0023e40921739e84eb51ca001
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236528"
---
### <a name="wpf-pointer-based-touch-stack"></a>WPF işaretçi tabanlı Touch yığını

|   |   |
|---|---|
|Ayrıntılar|Bu değişiklik, isteğe bağlı bir WM_POINTER sağlama yeteneği WPF dokunma/ekran kalemi yığın tabanlı ekler.  Bu açıkça olarak etkinleştirmeyin geliştiriciler WPF dokunma/ekran kalemi davranışında değişiklik görmeniz gerekir. Geçerli bilinen sorunları ile isteğe bağlı WM_POINTER dokunma/ekran kalemi yığın tabanlı:<ul><li>Gerçek zamanlı mürekkep desteği yoktur.</li><li>Mürekkep çalışırken ve StylusPlugIns çalışmaya devam eder, UI, düşük performansa neden olabilecek iş parçacığı üzerinde işlenir.</li><li>Davranış değişiklikleri nedeniyle değişiklikler, dokunma/ekran kalemi olaylardan yükseltmede fare olayları</li><li>İşleme farklı şekilde davranabilir</li><li>Sürükle ve bırak, dokunma girişini ilgili geri bildirim gösterilmez</li><li>İğne girişi etkilemez</li><li>Sürükle ve bırak, dokunma/ekran kalemi olayları artık başlatılabilir</li><li>Fare girişi algılandığında kadar bu uygulama potansiyel olarak askıda kalabilir.</li><li>Bunun yerine, geliştiriciler, sürükle başlatmak ve fare olayları bırakın.</li></ul>|
|Öneri|Bu yığın etkinleştirmek istediğiniz geliştiriciler ekleyin/kendi uygulamanın App.config dosyasına aşağıdaki birleştirme:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Bu kaldırma veya değerini false olarak ayarlayarak bu isteğe bağlı bir yığın kapanır. Bu yığın yalnızca Windows 10 Creators Update ve üzerinde kullanılabilir olduğunu unutmayın.|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Yeniden Hedefleme|
