---
title: ".NET Framework'te Tarih ve Saat Dizelerini Ayrıştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parsing strings, date and time strings
- date and time strings
- ParseExact method
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- DateTime object
- time strings
ms.assetid: 43bae51e-9b1d-41a6-a187-772c0d096d90
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1beceb2b2d32c500e73cd7786c480fcd84c3001c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-date-and-time-strings-in-net"></a>Tarih ve saat dizelerini .NET ayrıştırma
Ayrıştırma yöntemleri için eşdeğer bir tarih ve saat dize gösterimini Dönüştür <xref:System.DateTime> nesnesi. <xref:System.DateTime.Parse%2A> Ve <xref:System.DateTime.TryParse%2A> yöntemleri herhangi bir tarih ve saat birkaç ortak gösterimlerini Dönüştür. <xref:System.DateTime.ParseExact%2A> Ve <xref:System.DateTime.TryParseExact%2A> yöntemleri bir tarih ve saat biçim dizesi tarafından belirtilen desenle uyan bir dize gösterimi Dönüştür. (Konularına bakın [standart tarih ve saat biçim dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) ve [özel tarih ve saat biçim dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).)  
  
 Ayrıştırma tarih ve saat ayırıcılar ve ay, gün ve eras adları için kullanılan dizeler gibi bilgileri sağlayan bir biçim sağlayıcısı özellikleri tarafından etkilenir. Geçerli biçim sağlayıcısıdır <xref:System.Globalization.DateTimeFormatInfo> örtük olarak geçerli iş parçacığı kültürünü veya açıkça tarafından sağlanan nesne <xref:System.IFormatProvider> ayrıştırma yönteminin parametresi. İçin <xref:System.IFormatProvider> parametresini belirtin bir <xref:System.Globalization.CultureInfo> bir kültür temsil eder, nesne veya <xref:System.Globalization.DateTimeFormatInfo> nesnesi.  
  
 Ayrıştırılacak bir tarih dize gösterimini, ay ve en az bir gün veya yıl eklemeniz gerekir. Bir süre dize gösterimini saati içermelidir ve en az dakika veya AM/PM Belirleyicisi. Ancak, mümkünse belirtilmemişse bileşenleri için varsayılan değerleri sağlar ayrıştırma. Eksik tarihi geçerli tarihe kadar olan eksik bir yılın geçerli yıl, ay varsayılan olarak ayın ilk gününü eksik günün varsayılanlara Varsayılanları ve gece yarısına eksik birer varsayılanlarını.  
  
 Dize gösterimi yalnızca bir kez belirtiyorsa, döndürür ayrıştırma bir <xref:System.DateTime> nesnesi ile kendi <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, ve <xref:System.DateTime.Day%2A> karşılık gelen değerleri ayarlanan özellikleri <xref:System.DateTime.Today%2A> özelliği. Ancak, varsa <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> sabiti anahtarı belirtilmişse ayrıştırma yönteminin, sonuçta elde edilen yıl, ay ve gün özellikleri için değer ayarlayın `1`.  
  
 Bir tarih ve saat bileşeni ek olarak, bir tarih ve saat dize gösterimini ne kadar zaman Eşgüdümlü Evrensel Saat (UTC) öğesinden farklı gösteren uzaklığı içerebilir. Örneğin, dize "14/2/2007 5:32:00 -7:00" başka bir deyişle yedi saatler UTC'den önceki bir zaman tanımlar. Uzaklığı bir zaman dize gösterimini atlanırsa döndürür ayrıştırma bir <xref:System.DateTime> nesnesi ile kendi <xref:System.DateTime.Kind%2A> özelliğini <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>. Bir uzaklık belirtilirse, döndürür ayrıştırma bir <xref:System.DateTime> nesnesi ile kendi <xref:System.DateTime.Kind%2A> özelliğini <xref:System.DateTimeKind.Local> ve değerini makinenizde yerel saat dilimine ayarlanır. Kullanarak bu davranışı değiştirebilirsiniz bir <xref:System.Globalization.DateTimeStyles> ayrıştırma yöntemiyle sabit.  
  
 Biçim sağlayıcısı belirsiz bir sayısal tarihi yorumlamak için de kullanılır. Örneğin, hangi "03/02/04" dizeyle gösterilen tarih ay, gün ve yıl bileşenleridir açık değil. Bu durumda, bileşenleri, benzer tarih biçimleri biçimi sağlayıcısında sırasını göre değerlendirilir.  
  
## <a name="parse"></a>Ayrıştırma  
 Aşağıdaki kod örneğinde kullanımını göstermektedir **ayrıştırma** bir dizeye dönüştürmek için yöntem bir **DateTime**. Bu örnek, geçerli iş parçacığı ile ilişkili kültür ayrıştırma gerçekleştirmek için kullanır. Varsa <xref:System.Globalization.CultureInfo> geçerli ilişkili kültür giriş dizesini ayrıştıramıyor bir <xref:System.FormatException> oluşturulur.  
  
 [!code-csharp[Parsing.DateAndTime#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example.cs#1)]
 [!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example.vb#1)]  
  
 Ayrıca belirtebilirsiniz bir **CultureInfo** bu nesnesi tarafından tanımlanan kültürler ayarlamanıza veya standart birini belirtebilirsiniz <xref:System.Globalization.DateTimeFormatInfo> tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliği. Aşağıdaki kod örneğinde Almanca dizeye ayrıştırmak için biçim sağlayıcısı kullanan bir **DateTime**. A **CultureInfo** de-DE kültür temsil eden tanımlanan ve başarılı bu belirli dizesini ayrıştırma emin olmak için Ayrıştırılan dizesiyle geçirildi. Bu ayar ne olursa olsun önleyen **CurrentCulture** , **CurrentThread**.  
  
 [!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example2.cs#2)]
 [!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example2.vb#2)]  
  
 Ancak, aşırı kullanabilirsiniz ancak <xref:System.DateTime.Parse%2A> özel biçim sağlayıcıları belirtmek için yöntemi yöntemi standart biçim sağlayıcıları kullanımını desteklemez. Bir tarih ve saat standart olmayan bir biçimde ifade ayrıştırmak için kullanmak <xref:System.DateTime.ParseExact%2A> yöntemi yerine.  
  
 Aşağıdaki kod örneğinde <xref:System.Globalization.DateTimeStyles> geçerli tarih ve saat bilgilerini için eklenmemesi gerektiğini belirtmek için numaralandırma **DateTime** dize tanımlamaz alanlar için.  
  
 [!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example3.cs#3)]
 [!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example3.vb#3)]  
  
## <a name="parseexact"></a>ParseExact  
 <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> Yöntemi için belirtilen dize desenini uyan bir dize dönüştürür bir **DateTime** nesnesi. Bu yöntem için belirtilen biçimde değil bir dize geçirildiğinde bir <xref:System.FormatException> oluşturulur. Özel tarih ve saat biçim belirticileri sınırlı bir bileşimini veya standart tarih ve saat biçim belirticileri birini belirtebilirsiniz. Özel biçim belirticilerini kullanma, sizin için bir özel tanıma dizesi oluşturmak mümkündür. Üzerinde konular tanımlayıcıları açıklaması için bkz [standart tarih ve saat biçim dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) ve [özel tarih ve saat biçim dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).  
  
 Her aşırı yüklemesini <xref:System.DateTime.ParseExact%2A> yöntemi de sahip bir <xref:System.IFormatProvider> genellikle biçimlendirme kültüre özgü bilgileri dizesinin sağlar parametresi. Genellikle, bu <xref:System.IFormatProvider> nesne bir <xref:System.Globalization.CultureInfo> standart bir kültür temsil eden nesnesi veya bir <xref:System.Globalization.DateTimeFormatInfo> tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> özelliği. Ancak, diğer tarih ve saat işlevleri ayrıştırma, bu yöntem de destekleyen bir <xref:System.IFormatProvider> standart tarih ve saat biçimini tanımlar.  
  
 Aşağıdaki kod örneğinde, **ParseExact** yöntemi geçirilen ayrıştırmak için bir dize nesnesi ve ardından bir biçim belirticisi arkasından bir **CultureInfo** nesnesi. Bu **ParseExact** yöntemi yalnızca en-US kültür uzun tarih desende sergilemesine dizeleri ayrıştırma.  
  
 [!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example4.cs#4)]
 [!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example4.vb#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dizeleri ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)  
 [Biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md)  
 [.NET tür dönüştürme](../../../docs/standard/base-types/type-conversion.md)
