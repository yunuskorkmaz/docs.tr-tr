---
ms.openlocfilehash: 3709b9e694011666cebcb0ae09fbc838f65967af
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614870"
---
### <a name="wpf-grid-allocation-of-space-to-star-columns"></a>Boşluk-sütun için WPF ızgara alanı ayırma

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,7 ' den başlayarak WPF, <xref:System.Windows.Controls.Grid> boşluk alan ayırmak için kullanılan algoritmanın yerini alır \* . Bu, birkaç durumda atanan gerçek genişlik \* sütununu değiştirir:

- Bir veya daha fazla \* sütunda Ayrıca bu Sütu için orantılı ayırmayı geçersiz kılan en düşük veya en yüksek genişlik vardır. (En düşük genişlik açık bir MinWidth bildiriminden veya sütun içeriğinden elde edilen örtük bir en küçük değerden türetilebilir. Maksimum genişlik yalnızca bir MaxWidth bildiriminden açık olarak tanımlanabilir.)
- Bir veya daha fazla \* sütun, son derece büyük \* ağırlığa, 10 ^ 298 ' den büyük bir şekilde bildirir.
- \*-Ağırlıklar, kayan noktalı kararsızlık (taşma, yetersiz ve duyarlık kaybı) ile karşılaşmak için yeterince farklıdır.
- Düzen yuvarlama etkin olduğunda ve etkin görüntüleme DPı 'Sı yeterince yüksek olduğunda.
İlk iki durumda, yeni algoritma tarafından oluşturulan genişlikler eski algoritmadan üretilmiş olanlardan önemli ölçüde farklı olabilir; son durumda, fark en çok bir veya iki piksel olacaktır.<p/>Yeni algoritma, eski algoritmadaki çeşitli hataları düzeltir:

- Sütunlara toplam ayırma, kılavuzun genişliğini aşabilirler. Bu durum, orantılı payı en düşük boyuttan daha az olan bir sütuna alan ayrılırken meydana gelebilir. Algoritma en küçük boyutu ayırır, bu alan diğer sütunlara kullanılabilir alanı azaltır. \*Ayrılacak sütun yoksa, toplam ayırma çok büyük olur.
- Toplam ayırma, kılavuzun genişliğinin kısa bir kısmını alabilir. Bu, #1 için çift sorundur ve bu, değeri en büyük boyuttan daha büyük olan bir sütuna ayrılırken \* bolluk değerini almak için sütun kalmadı.
- İki sütunlu, \* ağırlıklarıyla orantılı olmayan ayırmaları alabilir \* . Bu, \* a-Columns a, B ve C sütunları ayrılırken (Bu sırada), b 'nin orantılı paylaşımının min (veya Max) kısıtlamasını ihlal ettiğini belirten #1/#2 'nin bir milder sürümüdür. Yukarıdaki gibi, bu, bir saniyeden daha az (veya daha fazla) orantılı ayırma alan C sütunu için kullanılabilir alanı değiştirir.
- Son derece büyük ağırlıklarla ( &gt; 10 ^ 298) oluşan sütunlar 10 ' a kadar ağırlığa sahip gibi davranır. Bunlar arasındaki orantılı farklılıklar (ve daha az kalınlıklarla sütunlar arasında) dikkate alınmamalıdır.
- Inifinte ağırlıklarını içeren sütunlar doğru işlenmez. [Aslında sonsuz olarak bir ağırlık ayarlayamazsınız, ancak bu yapay bir kısıtlamadır. Ayırma kodu, uygulamayı işlemeye çalışıyor, ancak hatalı iş yapıyor.]
- Taşma, yetersiz, kesinlik kaybı ve benzer kayan nokta sorunlarından kaçınırken birkaç küçük sorun.
- Düzen yuvarlama ayarlamaları, yeterince yüksek DPı 'de hatalı.
Yeni algoritma aşağıdaki ölçütlere uyan sonuçlar üretir:<p/>A. *-Sütununa atanan gerçek genişlik, en düşük genişliğinden veya en büyük genişliğinden daha büyük değildir.<br/>B. <em>Minimum veya maksimum genişliğine atanmamış her sütuna, ağırlığıyla orantılı bir genişlik atanır <em>. Kesin olması için, iki sütun sırasıyla genişlik x ve y ile bildirilirse</em> </em> ve sütun en küçük veya en büyük genişliğini alırsa, sütunlara atanan gerçek genişlik v ve w aynı orandır: v/w = = x/y.<br/>C. Orantılı sütunlara ayrılan toplam Genişlik &quot; , &quot; \* Kısıtlanmış sütunlara ayrıldıktan sonra kullanılabilir alana eşittir (sabit, otomatik ve \* -sütunlar, en düşük veya en büyük genişliği olarak tahsis edilir). Bu sıfır olabilir, örneğin minimum genişliklerin toplamı kılavuzun kullanılabilir genişliğini aşarsa.<br/>D. Tüm bu deyimler ideal düzene göre yorumlanacaktır &quot; &quot; . Düzen yuvarlama etkin olduğunda, gerçek genişlikler bir piksel kadar ideal genişliklerden farklı olabilir.<br/>Eski algoritma (A) kabul edilir ancak yukarıda özetlenen durumlarda diğer ölçütlere uyulmadı.<p/>Bu makaledeki sütunlar ve genişlikler hakkında söylenen her şey, satırlar ve yükseklikleri için de geçerlidir.

#### <a name="suggestion"></a>Öneri

Varsayılan olarak, .NET Framework 4,7 ' den başlayarak .NET Framework sürümlerini hedefleyen uygulamalar yeni algoritmayı görür, ancak .NET Framework 4.6.2 veya önceki sürümleri hedefleyen uygulamalar eski algoritmayı görür.<p/>Varsayılanı geçersiz kılmak için aşağıdaki yapılandırma ayarını kullanın:

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

Değer `true` eski algoritmayı seçer, `false` Yeni algoritmayı seçer.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4,7         |
| Tür    | Yeniden Hedefleme |
