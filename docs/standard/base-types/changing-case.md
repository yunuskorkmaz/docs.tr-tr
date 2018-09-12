---
title: .NET Framework'te Büyük/Küçük Harf Değiştirme
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd20db7fcc16f7781e093d59514c4be75705080a
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44514546"
---
# <a name="changing-case-in-net"></a>. NET'te değiştirme
Bir kullanıcı girişi kabul eden bir uygulama yazıyorsanız, hiçbir zaman isterse veri girmek için kullanacağı hangi çalışması emin olabilirsiniz. Genellikle, özellikle, bunların kullanıcı arabiriminde görüntülüyorsanız dizeleri tutarlı olarak büyük küçük harfleri istersiniz. Aşağıdaki tabloda, üç durum değiştirme yöntemleri açıklar. İlk iki yöntem bir kültür kabul eden bir aşırı yüklemesini sağlar.  
  
|Yöntem adı|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-----------------|---------|  
|<xref:System.String.ToUpper%2A?displayProperty=nameWithType>|Bir dizedeki tüm karakterleri büyük harfe dönüştürür.|  
|<xref:System.String.ToLower%2A?displayProperty=nameWithType>|Bir dizedeki tüm karakterleri küçük harfe dönüştürür.|  
|<xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>|Bir dize başlık harflere dönüştürür.|  
  
> [!WARNING]
>  Unutmayın <xref:System.String.ToUpper%2A?displayProperty=nameWithType> ve <xref:System.String.ToLower%2A?displayProperty=nameWithType> yöntemleri karşılaştırma veya bunları eşitlik için sınama için dizeleri dönüştürmek için kullanılmamalıdır. Daha fazla bilgi için [karşılaştırma büyük/küçük harf dizisini](#Comparing) bölümü.  
  
<a name="Comparing"></a>   
## <a name="comparing-strings-of-mixed-case"></a>Büyük/küçük harf, dizeleri karşılaştırma  
 Karma durumunu kendi sıralama belirlemek için dizeleri karşılaştırmak için bir aşırı yüklemelerinden birini çağırın <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yöntemi ile bir `comparisonType` parametresi ve değeri ya da sağlayın <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>, veya <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> için `comparisonType` bağımsız değişken. Bir karşılaştırması için geçerli kültür yerine belirli bir kültür kullanarak bir aşırı yüklemesini çağırmak <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yöntemi hem bir `culture` ve `options` parametresi ve değeri sağlayın <xref:System.Globalization.CompareOptions.IgnoreCase?displayProperty=nameWithType> olarak `options` bağımsız değişken.  
  
 Karma örneğinin eşit olup olmadığını belirlemek için dizeleri karşılaştırmak için kendi, aşırı yüklemelerinden çağırın <xref:System.String.Equals%2A?displayProperty=nameWithType> yöntemi ile bir `comparisonType` parametresi ve değeri ya da sağlar <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>, veya <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> için`comparisonType` bağımsız değişken.  
  
 Daha fazla bilgi için [kullanarak dizeleri için en iyi](../../../docs/standard/base-types/best-practices-strings.md).  
  
## <a name="toupper"></a>toUpper  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType> Yöntemi bir dizedeki tüm karakterleri büyük harfe değiştirir. Aşağıdaki örnek "Merhaba Dünya!" dize dönüştürür. büyük harfe karma çalışmasından.  
  
 [!code-csharp[Strings.ChangingCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#1)]
 [!code-vb[Strings.ChangingCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#1)]  
  
 Yukarıdaki örnekte kültüre duyarlıdır; varsayılan Bu, geçerli kültürün büyük/küçük harf kuralları geçerlidir. Kültüre duyarsız büyük/küçük bir değişiklik yapmak veya belirli bir kültürün büyük/küçük harf kuralları uygulamak için kullanma <xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini ve bir değeri sağlayın <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> veya <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> içinbelirtilenkültürütemsiledenbirnesne*kültür* parametresi. Nasıl kullanılacağını gösteren bir örnek <xref:System.String.ToUpper%2A> kültüre duyarsız büyük/küçük bir değişiklik yapmak için yöntemi bkz [kültüre duyarsız çalışması değişikliklerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="tolower"></a>toLower  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType> Yöntemi önceki yöntemine benzer, ancak bunun yerine bir dizedeki tüm karakterleri küçük harfe dönüştürür. Aşağıdaki örnek "Merhaba Dünya!" dize dönüştürür. küçük.  
  
 [!code-csharp[Strings.ChangingCase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#2)]
 [!code-vb[Strings.ChangingCase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#2)]  
  
 Yukarıdaki örnekte kültüre duyarlıdır; varsayılan Bu, geçerli kültürün büyük/küçük harf kuralları geçerlidir. Kültüre duyarsız büyük/küçük bir değişiklik yapmak veya belirli bir kültürün büyük/küçük harf kuralları uygulamak için kullanma <xref:System.String.ToLower%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini ve bir değeri sağlayın <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> veya <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> içinbelirtilenkültürütemsiledenbirnesne*kültür* parametresi. Nasıl kullanılacağını gösteren bir örnek <xref:System.String.ToLower%28System.Globalization.CultureInfo%29> kültüre duyarsız büyük/küçük bir değişiklik yapmak için yöntemi bkz [kültüre duyarsız çalışması değişikliklerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="totitlecase"></a>ToTitleCase  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> Her sözcüğün ilk karakteri ve kalan karakterler küçük harfe dönüştürür. Ancak, tamamen büyük harf olan sözcükleri kısaltmalar olarak kabul edilir ve dönüştürülmez.  
  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> Kültüre duyarlı bir yöntemdir; diğer bir deyişle, belirli bir kültürün büyük/küçük harf kurallarını kullanır. Yöntem çağırmak için önce aldığınız <xref:System.Globalization.TextInfo> belirli bir kültürün büyük/küçük harf kuralları temsil eden nesne <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> belirli bir kültürün özelliği.  
  
 Aşağıdaki örnekte, dizideki her bir dizenin geçirir <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> yöntemi.  Dizeleri kısaltmalar yanı sıra, uygun bir başlık dizeleri içerir. Dizeleri İngilizce (ABD) kültürünün büyük/küçük harf kurallarını kullanarak başlık harfe dönüştürülür.  
  
 [!code-csharp[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/cs/totitlecase2.cs#1)]
 [!code-vb[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/vb/totitlecase2.vb#1)]  
  
 Kültüre duyarlı olmasına rağmen dikkat <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> yöntemi dilsel olarak doğru büyük/küçük harf kuralları sağlamaz. Örneğin, önceki örnekte, yöntem "bir hikayesini iki şehirlerin" "A hikayesini, iki şehirlere" dönüştürür. Ancak, dilsel olarak doğru başlık büyük/küçük harf en-US kültürü için "Bir hikayesini iki şehirlerin." olur  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)  
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
