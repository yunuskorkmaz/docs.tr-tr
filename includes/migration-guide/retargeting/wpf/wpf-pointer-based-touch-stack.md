---
ms.openlocfilehash: 3463b6c45952aab0023e40921739e84eb51ca001
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859105"
---
### <a name="wpf-pointer-based-touch-stack"></a>WPF Pointer Tabanlı Dokunmatik Yığın

|   |   |
|---|---|
|Ayrıntılar|Bu değişiklik, isteğe bağlı WM_POINTER tabanlı WPF touch/stylus yığınını etkinleştirme özelliği ni ekler.  Bunu açıkça etkinleştirmeyen geliştiriciler WPF touch/stylus davranışında herhangi bir değişiklik görmemelidir. İsteğe bağlı WM_POINTER tabanlı dokunmatik/kalem yığını ile Güncel Bilinen Sorunlar:<ul><li>Gerçek zamanlı mürekkep için destek yok.</li><li>Mürekkep ve StylusPlugins hala çalışacak olsa da, onlar kötü performansa yol açabilir UI Thread üzerinde işlenir.</li><li>Dokunma/kalem etkinliklerinden fare olaylarına terfi değişiklikleri nedeniyle davranış değişiklikleri</li><li>Manipülasyon farklı davranabilir</li><li>Sürükle/Bırak, dokunma girişi için uygun geri bildirim göstermez</li><li>Bu, kalem girişietkilemez</li><li>Sürükle/Bırak artık dokunma/kalem olaylarında başlatılamaz</li><li>Bu, fare girişi algılanıncaya kadar uygulamayı asabilir.</li><li>Bunun yerine, geliştiriciler fare olaylarından sürükle ve bırak başlatmalıdır.</li></ul>|
|Öneri|Bu yığını etkinleştirmek isteyen geliştiriciler, uygulamalarının App.config dosyasına aşağıdakileri ekleyebilir/birleştirebilir:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Bunu kaldırmak veya değeri false olarak ayarlamak bu isteğe bağlı yığını kapatır. Bu yığının yalnızca Windows 10 Creators Update ve üzeri kullanılabilir durumda olduğunu unutmayın.|
|Kapsam|Edge|
|Sürüm|4.7|
|Tür|Yeniden Hedefleme|
