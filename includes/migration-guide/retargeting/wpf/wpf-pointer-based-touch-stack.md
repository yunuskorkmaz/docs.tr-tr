---
ms.openlocfilehash: bb3d7c1afa9e506ffc7c6d068c48428d1e66ccb6
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379441"
---
### <a name="wpf-pointer-based-touch-stack"></a>WPF işaretçi tabanlı Touch yığını

|   |   |
|---|---|
|Ayrıntılar|Bu değişiklik, isteğe bağlı bir WM_POINTER sağlama yeteneği WPF dokunma/ekran kalemi yığın tabanlı ekler.  Bu açıkça olarak etkinleştirmeyin geliştiriciler WPF dokunma/ekran kalemi davranışında değişiklik görmeniz gerekir. Geçerli bilinen sorunları ile isteğe bağlı WM_POINTER dokunma/ekran kalemi yığın tabanlı:<ul><li>Gerçek zamanlı mürekkep desteği yoktur.</li><li>Mürekkep çalışırken ve StylusPlugIns çalışmaya devam eder, UI, düşük performansa neden olabilecek iş parçacığı üzerinde işlenir.</li><li>Davranış değişiklikleri nedeniyle değişiklikler, dokunma/ekran kalemi olaylardan yükseltmede fare olayları</li><li>İşleme farklı şekilde davranabilir</li><li>Sürükle ve bırak, dokunma girişini ilgili geri bildirim gösterilmez</li><li>İğne girişi etkilemez</li><li>Sürükle ve bırak, dokunma/ekran kalemi olayları artık başlatılabilir</li><li>Bu durum uygulama fare girişi algılandığında kadar yanıt vermeyi durdurmasına neden olabilir.</li><li>Bunun yerine, geliştiriciler, sürükle başlatmak ve fare olayları bırakın.</li></ul>|
|Öneri|Bu yığın etkinleştirmek istediğiniz geliştiriciler ekleyin/kendi uygulamanın App.config dosyasına aşağıdaki birleştirme:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Bu kaldırma veya değerini false olarak ayarlayarak bu isteğe bağlı bir yığın kapanır. Bu yığın yalnızca Windows 10 Creators Update ve üzerinde kullanılabilir olduğunu unutmayın.|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Yeniden Hedefleme|
