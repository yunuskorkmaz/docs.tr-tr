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
ms.custom: seodec18
ms.openlocfilehash: a8eb45e45a905f0b366642050f4845460e14aaf8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132900"
---
# <a name="changing-case-in-net"></a>.NET ' te durum değiştirme
Bir kullanıcıdan girişi kabul eden bir uygulama yazarsanız, ya da kendisinin verileri girerken kullanacağı durumda hiçbir şekilde emin olabilirsiniz. Genellikle, özellikle de Kullanıcı arabiriminde görüntülüyorsanız, dizelerin tutarlı bir şekilde kullanılabilir olmasını istersiniz. Aşağıdaki tabloda üç büyük/küçük harf değiştirme yöntemi açıklanmaktadır. İlk iki yöntem kültürü kabul eden bir aşırı yükleme sağlar.  
  
|Yöntem adı|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-----------------|---------|  
|<xref:System.String.ToUpper%2A?displayProperty=nameWithType>|Dizedeki tüm karakterleri büyük harfe dönüştürür.|  
|<xref:System.String.ToLower%2A?displayProperty=nameWithType>|Dizedeki tüm karakterleri küçük harfe dönüştürür.|  
|<xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>|Bir dizeyi başlık örneğine dönüştürür.|  
  
> [!WARNING]
> <xref:System.String.ToUpper%2A?displayProperty=nameWithType> ve <xref:System.String.ToLower%2A?displayProperty=nameWithType> yöntemlerinin, bunları karşılaştırmak veya eşitlik için test etmek üzere dizeleri dönüştürmek için kullanılmamalıdır. Daha fazla bilgi için bkz. [karışık büyük/küçük harfe yönelik dizeleri karşılaştırma](#Comparing) bölümü.  
  
<a name="Comparing"></a>   
## <a name="comparing-strings-of-mixed-case"></a>Karışık durum dizelerini karşılaştırma  
 Sıralamalarını tespit etmek için karışık durum dizelerini karşılaştırmak için, <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yönteminin aşırı yüklerini bir `comparisonType` parametresiyle çağırın ve <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> bağımsız değişkeni olarak <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>veya `comparisonType` değerini sağlayın. Geçerli kültür dışındaki belirli bir kültürü kullanan bir karşılaştırma için, <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yönteminin bir `culture` ve `options` parametresiyle birlikte bir yüklemesini çağırın ve `options` bağımsız değişkeni olarak <xref:System.Globalization.CompareOptions.IgnoreCase?displayProperty=nameWithType> değeri sağlayın.  
  
 Eşit olup olmadıklarını anlamak için karışık büyük/küçük harf dizelerini karşılaştırmak için, <xref:System.String.Equals%2A?displayProperty=nameWithType> yönteminin aşırı yüklerini bir `comparisonType` parametresiyle çağırın ve <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> bağımsız değişkeni olarak <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>veya `comparisonType` değerini sağlayın.  
  
 Daha fazla bilgi için bkz. [dizeleri kullanmak Için En Iyi uygulamalar](../../../docs/standard/base-types/best-practices-strings.md).  
  
## <a name="toupper"></a>toUpper  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType> yöntemi bir dizedeki tüm karakterleri büyük harfe dönüştürür. Aşağıdaki örnek "Merhaba Dünya!" dizesini dönüştürür Karma durumundan büyük harfe kadar.  
  
 [!code-csharp[Strings.ChangingCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#1)]
 [!code-vb[Strings.ChangingCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#1)]  
  
 Yukarıdaki örnek, varsayılan olarak kültüre duyarlıdır; geçerli kültürün büyük/küçük harf kurallarını uygular. Kültüre duyarsız bir durum değişikliği gerçekleştirmek veya belirli bir kültürün büyük/küçük harf kurallarını uygulamak için <xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini kullanın ve bir <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> değeri ya da belirtilen kültürü temsil eden bir <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> nesnesi *kültür* parametresine girin . Kültüre duyarsız bir durum değişikliği gerçekleştirmek üzere <xref:System.String.ToUpper%2A> yönteminin nasıl kullanılacağını gösteren bir örnek için, bkz. [kültüre duyarsız büyük/küçük harf değişiklikleri gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="tolower"></a>toLower  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType> yöntemi Previous yöntemine benzer, ancak bunun yerine dizedeki tüm karakterleri küçük harfe dönüştürür. Aşağıdaki örnek "Merhaba Dünya!" dizesini dönüştürür küçük harfe Dönüştür.  
  
 [!code-csharp[Strings.ChangingCase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#2)]
 [!code-vb[Strings.ChangingCase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#2)]  
  
 Yukarıdaki örnek, varsayılan olarak kültüre duyarlıdır; geçerli kültürün büyük/küçük harf kurallarını uygular. Kültüre duyarsız bir durum değişikliği gerçekleştirmek veya belirli bir kültürün büyük/küçük harf kurallarını uygulamak için <xref:System.String.ToLower%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini kullanın ve bir <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> değeri ya da belirtilen kültürü temsil eden bir <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> nesnesi *kültür* parametresine girin . Kültüre duyarsız bir durum değişikliği gerçekleştirmek üzere <xref:System.String.ToLower%28System.Globalization.CultureInfo%29> yönteminin nasıl kullanılacağını gösteren bir örnek için, bkz. [kültüre duyarsız büyük/küçük harf değişiklikleri gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="totitlecase"></a>ToTitleCase  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> her sözcüğün ilk karakterini büyük harfe ve geri kalan karakterleri küçük harfe dönüştürür. Ancak, tamamen büyük harfli sözcüklerin kısaltmalar olduğu ve dönüştürülmemekte olduğu varsayılır.  
  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> yöntemi kültüre duyarlıdır; diğer bir deyişle, belirli bir kültürün büyük/küçük harf kurallarını kullanır. Yöntemi çağırmak için, ilk olarak belirli bir kültürün <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> özelliğinden belirli bir kültürün büyük/küçük harf kurallarını temsil eden <xref:System.Globalization.TextInfo> nesnesini alırsınız.  
  
 Aşağıdaki örnek, bir dizideki her dizeyi <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> yöntemine geçirir.  Dizeler, doğru başlık dizelerini ve kısaltmalardan de yer alır. Dizeler, Ingilizce (Birleşik Devletler) kültürün büyük/küçük harf kuralları kullanılarak başlık örneğine dönüştürülür.  
  
 [!code-csharp[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/cs/totitlecase2.cs#1)]
 [!code-vb[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/vb/totitlecase2.vb#1)]  
  
 Kültüre duyarlı olsa da <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> yöntemi dilsel doğru büyük/küçük harf kuralları sağlamayacağını unutmayın. Örneğin, önceki örnekte, yöntemi "bir Tale iki şehir" olarak "bir Tale Iki şehir" olarak dönüştürür. Ancak, en-US kültürü için dilsel doğru başlık büyük küçük harfleri "bir Tale Iki şehir" dir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
