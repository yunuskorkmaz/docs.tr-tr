---
ms.openlocfilehash: eb89cbc72d8b09fd1aa5bc775a6c539eb208fa70
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614898"
---
### <a name="wpf-pointer-based-touch-stack"></a>WPF Işaretçi tabanlı dokunmatik yığın

#### <a name="details"></a>Ayrıntılar

Bu değişiklik, isteğe bağlı WM_POINTER tabanlı WPF dokunmatik/Stilus yığınını etkinleştirme özelliği ekler.  Bunu açıkça etkinleştirmesiz geliştiriciler WPF dokunma/ekran kalemi davranışında değişiklik görmez. İsteğe bağlı WM_POINTER tabanlı dokunma/ekran kalemi yığınında bilinen geçerli sorunlar:

- Gerçek zamanlı mürekkep oluşturma desteği yoktur.
- Mürekkep oluşturma ve StylusPlugIns çalışmaya devam ederken, Kullanıcı arabirimi Iş parçacığında işlenecektir ve bu da kötü performansa neden olabilir.
- Dokunmatik/ekran kalemi olaylarından fare olaylarına yükseltme yapılan değişiklikler nedeniyle davranış değişiklikleri
- Düzenleme farklı davranabilirler
- Sürükle/bırak, dokunma girişi için uygun geri bildirimi göstermez
- Bu, ekran kalemi girişini etkilemez
- Sürükle/bırak, artık dokunmatik/ekran kalemi olaylarında başlatılamaz
- Bu, fare girişi algılanana kadar uygulamanın askıda kalmasına yol açabilir.
- Bunun yerine, geliştiriciler fare olaylarından sürükle ve bırak işlemini başlatmalıdır.

#### <a name="suggestion"></a>Öneri

Bu yığını etkinleştirmek isteyen geliştiriciler, uygulamanın App.config dosyasına aşağıdakileri ekleyebilir/birleştirebilir:

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

Bu değer kaldırıldığında veya false olarak ayarlandığında, bu isteğe bağlı yığın kapanır. Bu yığının yalnızca Windows 10 Creators Update ve üzeri sürümlerde kullanılabilir olduğunu unutmayın.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4,7         |
| Tür    | Yeniden Hedefleme |
