---
title: .NET ' te durum değiştirme
description: .NET 'teki dizeler söz konusu olduğunda nasıl değiştirileceğini öğrenin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], case
- case sensitivity
- ToUpper method
- ToLower method
- uppercase
- lowercase
ms.assetid: 6805f81b-e9ad-4387-9f4c-b9bdb21b87c0
ms.openlocfilehash: e838d6df778802d7eaab3f12205698cc6ca5f72b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290597"
---
# <a name="change-case-in-net"></a>.NET 'teki durumu değiştir

Bir kullanıcıdan girişi kabul eden bir uygulama yazarsanız, verileri girerken ne durumda (büyük veya daha düşük) bir şekilde emin olabilirsiniz. Genellikle, özellikle de Kullanıcı arabiriminde görüntülüyorsanız, dizelerin tutarlı bir şekilde kullanılabilir olmasını istersiniz. Aşağıdaki tabloda üç büyük/küçük harf değiştirme yöntemi açıklanmaktadır. İlk iki yöntem kültürü kabul eden bir aşırı yükleme sağlar.  
  
|Yöntem adı|Kullanım|  
|-----------------|---------|  
|<xref:System.String.ToUpper%2A?displayProperty=nameWithType>|Dizedeki tüm karakterleri büyük harfe dönüştürür.|  
|<xref:System.String.ToLower%2A?displayProperty=nameWithType>|Dizedeki tüm karakterleri küçük harfe dönüştürür.|  
|<xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>|Bir dizeyi başlık örneğine dönüştürür.|  
  
> [!WARNING]
> <xref:System.String.ToUpper%2A?displayProperty=nameWithType>Ve <xref:System.String.ToLower%2A?displayProperty=nameWithType> yöntemlerinin, bunları karşılaştırmak veya eşitlik için test etmek üzere dizeleri dönüştürmek için kullanılması gerektiğini unutmayın. Daha fazla bilgi için bkz. [karışık büyük/küçük harfe yönelik dizeleri karşılaştırma](#Comparing) bölümü.  
  
<a name="Comparing"></a>
## <a name="compare-strings-of-mixed-case"></a>Karışık durum dizelerini karşılaştırın  

 Sıralamalarını tespit etmek için karışık büyük/küçük harf dizelerini karşılaştırmak için, <xref:System.String.CompareTo%2A?displayProperty=nameWithType> bir parametresiyle yöntemin aşırı yüklerini çağırın `comparisonType` ve ya da <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> `comparisonType` bağımsız değişken için bir değer sağlayın. Geçerli kültür dışındaki belirli bir kültürü kullanan bir karşılaştırma için, yönteminin hem hem de parametresiyle birlikte bir aşırı yüklemesini çağırın <xref:System.String.CompareTo%2A?displayProperty=nameWithType> `culture` `options` ve <xref:System.Globalization.CompareOptions.IgnoreCase?displayProperty=nameWithType> bağımsız değişken olarak bir değer sağlayın `options` .  
  
 Eşit olup olmadıklarını tespit etmek için karışık büyük/küçük harf dizelerini karşılaştırmak için, bir parametresiyle yöntemin aşırı yüklemelerinin birini çağırın <xref:System.String.Equals%2A?displayProperty=nameWithType> `comparisonType` ve <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> , <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> veya <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> `comparisonType` bağımsız değişken için bir değer sağlayın.  
  
 Daha fazla bilgi için bkz. [dizeleri kullanmak Için En Iyi uygulamalar](best-practices-strings.md).  
  
## <a name="toupper"></a>ToUpper  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>Yöntemi bir dizedeki tüm karakterleri büyük harfe dönüştürür. Aşağıdaki örnek "Merhaba Dünya!" dizesini dönüştürür Karma durumundan büyük harfe kadar.  
  
 [!code-csharp[Strings.ChangingCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#1)]
 [!code-vb[Strings.ChangingCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#1)]  
  
 Yukarıdaki örnek, varsayılan olarak kültüre duyarlıdır; geçerli kültürün büyük/küçük harf kurallarını uygular. Kültüre duyarsız bir durum değişikliği gerçekleştirmek veya belirli bir kültürün büyük/küçük harf kurallarını uygulamak için, <xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> yöntem aşırı yüklemesini kullanın ve bir değeri <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> ya da <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> belirtilen kültürü temsil eden bir nesneyi *kültür* parametresine girin. <xref:System.String.ToUpper%2A>Kültüre duyarsız bir durum değişikliği gerçekleştirmek için yönteminin nasıl kullanılacağını gösteren bir örnek için, bkz. [kültüre duyarsız büyük/küçük harf değişiklikleri gerçekleştirme](../globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="tolower"></a>ToLower  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType>Yöntemi önceki yönteme benzerdir, ancak bunun yerine dizedeki tüm karakterleri küçük harfe dönüştürür. Aşağıdaki örnek "Merhaba Dünya!" dizesini dönüştürür küçük harfe Dönüştür.  
  
 [!code-csharp[Strings.ChangingCase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#2)]
 [!code-vb[Strings.ChangingCase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#2)]  
  
 Yukarıdaki örnek, varsayılan olarak kültüre duyarlıdır; geçerli kültürün büyük/küçük harf kurallarını uygular. Kültüre duyarsız bir durum değişikliği gerçekleştirmek veya belirli bir kültürün büyük/küçük harf kurallarını uygulamak için, <xref:System.String.ToLower%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> yöntem aşırı yüklemesini kullanın ve bir değeri <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> ya da <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> belirtilen kültürü temsil eden bir nesneyi *kültür* parametresine girin. <xref:System.String.ToLower%28System.Globalization.CultureInfo%29>Kültüre duyarsız bir durum değişikliği gerçekleştirmek için yönteminin nasıl kullanılacağını gösteren bir örnek için, bkz. [kültüre duyarsız büyük/küçük harf değişiklikleri gerçekleştirme](../globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="totitlecase"></a>ToTitleCase  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>Her sözcüğün ilk karakterini büyük harfe ve geri kalan karakterleri küçük harfe dönüştürür. Ancak, tamamen büyük harfli sözcüklerin kısaltmalar olduğu ve dönüştürülmemekte olduğu varsayılır.  
  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>Yöntem kültüre duyarlıdır; diğer bir deyişle, belirli bir kültürün büyük/küçük harf kurallarını kullanır. Yöntemi çağırmak için, ilk olarak belirli <xref:System.Globalization.TextInfo> bir kültürün özelliğinden belirli bir kültürün büyük/küçük harf kurallarını temsil eden nesneyi alırsınız <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> .  
  
 Aşağıdaki örnek, bir dizideki her dizeyi <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> yöntemine geçirir.  Dizeler, doğru başlık dizelerini ve kısaltmalardan de yer alır. Dizeler, Ingilizce (Birleşik Devletler) kültürün büyük/küçük harf kuralları kullanılarak başlık örneğine dönüştürülür.  
  
 [!code-csharp[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/cs/totitlecase2.cs#1)]
 [!code-vb[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/vb/totitlecase2.vb#1)]  
  
 Kültüre duyarlı olsa da, <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> yöntemin dilsel doğru büyük/küçük harf kuralları sağlamayacağını unutmayın. Örneğin, önceki örnekte, yöntemi "bir Tale iki şehir" olarak "bir Tale Iki şehir" olarak dönüştürür. Ancak, en-US kültürü için dilsel doğru başlık büyük küçük harfleri "bir Tale Iki şehir" dir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel dize Işlemleri](basic-string-operations.md)
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../globalization-localization/performing-culture-insensitive-string-operations.md)
