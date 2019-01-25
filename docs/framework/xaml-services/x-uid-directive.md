---
title: x:Uid Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: 361240c2d2c140c7bf521ece423df4aaed075ba4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745421"
---
# <a name="xuid-directive"></a>x:Uid Yönergesi
Biçimlendirme öğesi için benzersiz bir tanımlayıcı sağlar. Birçok senaryoda bu benzersiz tanımlayıcı XAML yerelleştirme işlemleri ve araçları tarafından kullanılır.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object x:Uid="identifier"... />  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`identifier`|El ile oluşturulmuş bir ya da olarak yorumlandığında, bir dosyada benzersiz olması gereken otomatik olarak oluşturulan dize bir `x:Uid` tüketici.|  
  
## <a name="remarks"></a>Açıklamalar  
 [MS-XAML] içinde `x:Uid` bir yönerge tanımlanır. Daha fazla bilgi için [ \[MS-XAML\] bölümü 5.3.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
 `x:Uid` öğesinden farklı `x:Name` hem belirtilen XAML yerelleştirme senaryosu nedeniyle ve yerelleştirme için kullanılan tanımlayıcıları üzerinde programlama modeli etkilerini bağımlılık edinecek olmanızdır `x:Name`. Ayrıca, `x:Name` XAML namescope tarafından; tabidir ancak `x:Uid` benzersizlik zorlama tüm XAML tanımlı dil kavramını tarafından yönetilmeyen. XAML işlemci genel anlamda (yerelleştirme işleminin bir parçası olmayan işlemci) beklenmiyordu benzersizliğini zorlamak için `x:Uid` değerleri. Bu kavramsal olarak gönderene değerleri, üzerinde sorumluluğundadır. Benzersizliğini beklentisi `x:Uid` adanmış Genelleştirme işlemleri veya Araçlar gibi değerler Tüketiciler için makul tek bir XAML kaynağı içindeki değerleri. Tipik bir Benzersizlik modeli olan `x:Uid` değerleri XAML temsil eden bir XML kodlu dosyası içinde benzersizdir.  
  
 Belirli bir XAML şema önemli bilgisine sahip araçları uygulamak seçebilirsiniz `x:Uid` için yalnızca true yerelleştirilebilir dize yerine bir metin dizesi değeri işaretlemede karşılaştı burada tüm durumlarda.  
  
 Çerçeveleri belirli bir özellik için bir diğer ad olarak kendi nesne modelinde belirtebilirsiniz `x:Uid` özniteliği uygulayarak <xref:System.Windows.Markup.UidPropertyAttribute> tanımlama türü. Belirli bir özelliği bir çerçeve belirtiyorsa, her ikisini de belirtmek için geçerli değil `x:Uid` ve diğer adlı üye aynı nesne üzerinde. Her iki `x:Uid` ve belirtilen diğer adlı üye, .NET Framework XAML Hizmetleri API genellikle oluşturur <xref:System.Xaml.XamlDuplicateMemberException> bu durum için.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 Rolü hakkında daha fazla bilgi için `x:Uid` WPF yerelleştirme işleminde ve XAML BAML biçiminde görmek [WPF için genelleştirme](../../../docs/framework/wpf/advanced/globalization-for-wpf.md) veya <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [WPF için Genelleştirme](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
