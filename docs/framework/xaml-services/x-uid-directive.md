---
title: "x:Uid Yönergesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
caps.latest.revision: "12"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 4d49e9630b481b2daf103feabd225dd5ef0c8ca2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xuid-directive"></a>x:Uid Yönergesi
Benzersiz bir tanımlayıcı için işaretleme öğeleri sağlar. XAML yerelleştirme işlemleri ve araçları tarafından birçok senaryoda bu benzersiz tanımlayıcı kullanılır.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object x:Uid="identifier"... />  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`identifier`|El ile oluşturulmuş bir ya da tarafından değerlendirdiğinde, bir dosyada benzersiz olması gereken otomatik olarak oluşturulur dize bir `x:Uid` tüketici.|  
  
## <a name="remarks"></a>Açıklamalar  
 [MS-XAML] içinde `x:Uid` bir yönerge tanımlanır. Daha fazla bilgi için bkz: [ \[MS XAML\] bölüm 5.3.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
 `x:Uid`öğesinden farklı `x:Name` hem belirtilen XAML yerelleştirme senaryosu nedeniyle ve yerelleştirme için kullanılan tanımlayıcıları bağımlılık üzerinde programlama modeli etkilerini böylece `x:Name`. Ayrıca, `x:Name` XAML isim alanı tarafından; tabidir ancak `x:Uid` herhangi XAML dil tanımlanmış kavramı benzersizlik zorlama tarafından yönetilmeyen. XAML işlemcileri geniş herkese açık (yerelleştirme işleminin bir parçası olmayan işlemciler) beklendiği benzersizliğini zorlamak için `x:Uid` değerleri. Bu kavramsal olarak gönderenin değerlerin sorumluluğundadır. Benzersizliğini beklentisi `x:Uid` tek bir XAML kaynağı içindeki değerleri tüketiciler ayrılmış Genelleştirme işlemler veya araçları gibi değerler için makul. Tipik benzersizlik modeli olan `x:Uid` değerleri XAML temsil eden bir XML kodlu dosya içinde benzersizdir.  
  
 Belirli bir XAML şema önemli bilgilere sahip araçları uygulamak seçebilirsiniz `x:Uid` yalnızca true yerelleştirilebilir dizeler yerine tüm durumlarda burada bir metin dizesi değeri karşılaştı biçimlendirme.  
  
 Çerçeveler belirli bir özellik için bir diğer ad olarak kendi nesne modelinde belirtebilirsiniz `x:Uid` öznitelik uygulayarak <xref:System.Windows.Markup.UidPropertyAttribute> tanımlayıcı türü. Bir çerçeve belirli bir özellik belirtiyorsa, her ikisi de belirtmek için geçerli değil `x:Uid` ve diğer üye aynı nesne üzerinde. Her iki `x:Uid` ve diğer üye belirtilirse, .NET Framework XAML Hizmetleri API genellikle oluşturur <xref:System.Xaml.XamlDuplicateMemberException> bu durumda.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 Rolü hakkında daha fazla bilgi için `x:Uid` WPF yerelleştirme işleminde ve XAML BAML biçiminde bkz [WPF için genelleştirme](../../../docs/framework/wpf/advanced/globalization-for-wpf.md) veya<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
 <xref:Microsoft.Build.Tasks.Windows.UidManager>  
 [WPF için genelleştirme](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
