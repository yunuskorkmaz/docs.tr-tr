---
title: .NET'te Büyük/Küçük Harf Değiştirme
description: .NET'teki dizeleri durumunda nasıl değiştireceğinizi öğrenin.
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
ms.openlocfilehash: 19795cbed27ca979af813b6060163e76fc5b3780
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187221"
---
# <a name="change-case-in-net"></a>.NET'te büyük/küçük harf değiştirme

Bir kullanıcıdan giriş kabul eden bir uygulama yazarsanız, verileri girmek için hangi durumda (üst veya alt) kullanacaklarından asla emin olamazsınız. Genellikle, dizeleri tutarlı bir şekilde, özellikle de kullanıcı arabiriminde görüntüleniyorsanız durumda olmak istiyorum. Aşağıdaki tabloda üç büyük/küçük harf değiştirme yöntemi açıklanmaktadır. İlk iki yöntem, bir kültürü kabul eden aşırı yük sağlar.  
  
|Yöntem adı|Kullanım|  
|-----------------|---------|  
|<xref:System.String.ToUpper%2A?displayProperty=nameWithType>|Dizedeki tüm karakterleri büyük harfe dönüştürür.|  
|<xref:System.String.ToLower%2A?displayProperty=nameWithType>|Dizedeki tüm karakterleri küçük harfe dönüştürür.|  
|<xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>|Bir dizeyi başlık örneğine dönüştürür.|  
  
> [!WARNING]
> <xref:System.String.ToUpper%2A?displayProperty=nameWithType> Ve <xref:System.String.ToLower%2A?displayProperty=nameWithType> yöntemlerin dizeleri karşılaştırmak veya eşitlik için sınamak için dönüştürmek için kullanılmaması gerektiğini unutmayın. Daha fazla bilgi için [karışık büyük/küçük harf bölümünün Karşılaştırma dizelerine](#Comparing) bakın.  
  
<a name="Comparing"></a>
## <a name="compare-strings-of-mixed-case"></a>Karışık büyük/küçük harf dizelerini karşılaştırın  

 Sıralamalarını belirlemek için karışık servis talebi dizelerini <xref:System.String.CompareTo%2A?displayProperty=nameWithType> karşılaştırmak `comparisonType` <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> için, yöntemin aşırı yüklerinden birini parametreyle arayın `comparisonType` ve bağımsız değişken için bir değer sağlayın. Geçerli kültür dışındaki belirli bir kültürü kullanarak karşılaştırma için, <xref:System.String.CompareTo%2A?displayProperty=nameWithType> hem `culture` a hem `options` de parametre ile <xref:System.Globalization.CompareOptions.IgnoreCase?displayProperty=nameWithType> yöntemin `options` aşırı yüklenmesini çağırın ve bağımsız değişken olarak bir değer sağlayın.  
  
 Eşit olup <xref:System.String.Equals%2A?displayProperty=nameWithType> olmadıklarını belirlemek `comparisonType` <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> için karışık büyük/küçük harf dizelerini karşılaştırmak için, yöntemin aşırı yüklerinden birini parametreyle `comparisonType` arayın ve bağımsız değişken için bir değer sağlayın.  
  
 Daha fazla bilgi [için, Dizeleri Kullanmak için En İyi Uygulamalar'a](../../../docs/standard/base-types/best-practices-strings.md)bakın.  
  
## <a name="toupper"></a>Toupper  
 Yöntem, <xref:System.String.ToUpper%2A?displayProperty=nameWithType> bir dizedeki tüm karakterleri büyük harfe değiştirir. Aşağıdaki örnek "Hello World!" dizesini dönüştürür. karışık durumdan büyük harfe kadar.  
  
 [!code-csharp[Strings.ChangingCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#1)]
 [!code-vb[Strings.ChangingCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#1)]  
  
 Önceki örnek varsayılan olarak kültüre duyarlıdır; mevcut kültürün kasa kurallarını uygular. Kültüre duyarsız bir durum değişikliği gerçekleştirmek veya belirli bir kültürün kasa kurallarını <xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> uygulamak için, aşırı <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> yükleme <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> yöntemini kullanın ve kültür *parametresine* belirtilen kültürü temsil eden bir değer veya nesnenin değerini veya değerini verin. Kültüre duyarlı bir servis talebi <xref:System.String.ToUpper%2A> değişikliği gerçekleştirmek için yöntemin nasıl kullanılacağını gösteren bir örnek [için](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)bkz.  
  
## <a name="tolower"></a>Tolower  
 Yöntem <xref:System.String.ToLower%2A?displayProperty=nameWithType> önceki yönteme benzer, ancak bunun yerine bir dizedeki tüm karakterleri küçük harfe dönüştürür. Aşağıdaki örnek "Hello World!" dizesini dönüştürür. küçük düşürmek için.  
  
 [!code-csharp[Strings.ChangingCase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#2)]
 [!code-vb[Strings.ChangingCase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#2)]  
  
 Önceki örnek varsayılan olarak kültüre duyarlıdır; mevcut kültürün kasa kurallarını uygular. Kültüre duyarsız bir durum değişikliği gerçekleştirmek veya belirli bir kültürün kasa kurallarını <xref:System.String.ToLower%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> uygulamak için, aşırı <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> yükleme <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> yöntemini kullanın ve kültür *parametresine* belirtilen kültürü temsil eden bir değer veya nesnenin değerini veya değerini verin. Kültüre duyarlı bir servis talebi <xref:System.String.ToLower%28System.Globalization.CultureInfo%29> değişikliği gerçekleştirmek için yöntemin nasıl kullanılacağını gösteren bir örnek [için](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)bkz.  
  
## <a name="totitlecase"></a>Başlık Case  
 Her <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> sözcüğün ilk karakterini büyük harfe, kalan karakterleri küçük harfe dönüştürür. Ancak, tamamen büyük harfli sözcüklerin kısaltma olduğu varsayılır ve dönüştürülmez.  
  
 Yöntem <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> kültüre duyarlıdır; diğer bir şey, belirli bir kültürün kasa kurallarını kullanır. Yöntemi çağırmak için, önce belirli <xref:System.Globalization.TextInfo> bir kültürün kasa kurallarını temsil eden nesneyi <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> belirli bir kültürün özelliğinden alırsınız.  
  
 Aşağıdaki örnek, bir dizideki her <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> dizeyi yönteme geçirir.  Dizeleri uygun başlık dizeleri yanı sıra kısaltmalar içerir. Dizeleri, İngilizce (ABD) kültürünün kasa kuralları kullanılarak başlık örneğine dönüştürülür.  
  
 [!code-csharp[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/cs/totitlecase2.cs#1)]
 [!code-vb[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/vb/totitlecase2.vb#1)]  
  
 Kültüre duyarlı olmasına rağmen, <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> yöntemin dilsel olarak doğru kasa kuralları sağlamadığını unutmayın. Örneğin, önceki örnekte, yöntem "iki şehrin öyküsü"nu "İki Şehrin Hikayesi"ne dönüştürür. Ancak, en-ABD kültürü için dilsel olarak doğru başlık kaplama "İki Şehrin Hikayesi" dir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
