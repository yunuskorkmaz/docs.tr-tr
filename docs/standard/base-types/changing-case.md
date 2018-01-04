---
title: ".NET Framework'te Büyük/Küçük Harf Değiştirme"
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
- strings [.NET Framework], case
- case sensitivity
- ToUpper method
- ToLower method
- uppercase
- lowercase
ms.assetid: 6805f81b-e9ad-4387-9f4c-b9bdb21b87c0
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a3d845f53238f3b5b1744c13de9800e0d8f65dbc
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="changing-case-in-net"></a>.NET durumda değiştirme
Bir kullanıcıdan giriş kabul eden bir uygulama yazıyorsanız, hiçbir zaman çözemiyorsa veri girmek için kullanacağı hangi durumda emin olabilirsiniz. Genellikle, özellikle, bunları kullanıcı arabiriminde görüntülüyorsanız tutarlı olarak ortası dizeleri istiyor. Aşağıdaki tabloda, üç durumda değiştirme yöntemleri açıklar. İlk iki yöntem bir kültür kabul eden bir aşırı sağlar.  
  
|Yöntem adı|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-----------------|---------|  
|<xref:System.String.ToUpper%2A?displayProperty=nameWithType>|Bir dize içindeki tüm karakterleri büyük harfe dönüştürür.|  
|<xref:System.String.ToLower%2A?displayProperty=nameWithType>|Bir dize içindeki tüm karakterleri küçük harfe dönüştürür.|  
|<xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>|Bir dize başlık harfli biçime dönüştürür.|  
  
> [!WARNING]
>  Unutmayın <xref:System.String.ToUpper%2A?displayProperty=nameWithType> ve <xref:System.String.ToLower%2A?displayProperty=nameWithType> yöntemleri bunları karşılaştırmak ya da eşitlik için test amacıyla dizelerini dönüştürmek için kullanılmamalıdır. Daha fazla bilgi için bkz: [büyük/küçük harf dizeleri karşılaştırma](#Comparing) bölümü.  
  
<a name="Comparing"></a>   
## <a name="comparing-strings-of-mixed-case"></a>Büyük/küçük harf dizeleri karşılaştırma  
 Kendi sıralama belirlemek için büyük/küçük harf dizeleri karşılaştırmak için aşırı birini çağırın <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yöntemi ile bir `comparisonType` parametresi ve ya da değerini sağlamalısınız <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>, veya <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> için `comparisonType` bağımsız değişken. Bir karşılaştırma için bir aşırı yüklemesini çağırın geçerli kültürü dışında bir kültürü kullanarak <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yöntemi hem bir `culture` ve `options` parametresi ve değeri sağlayın <xref:System.Globalization.CompareOptions.IgnoreCase?displayProperty=nameWithType> olarak `options` bağımsız değişkeni.  
  
 Eşit olup olmadıklarını belirlemek için büyük/küçük harf dizeleri karşılaştırmak için kendi, aşırı birini çağırın <xref:System.String.Equals%2A?displayProperty=nameWithType> yöntemi ile bir `comparisonType` parametresi ve ya da değerini sağlamalısınız <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>, veya <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> için`comparisonType` bağımsız değişkeni.  
  
 Daha fazla bilgi için bkz: [kullanarak dizeleri için en iyi uygulamaları](../../../docs/standard/base-types/best-practices-strings.md).  
  
## <a name="toupper"></a>toUpper  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType> Yöntemi bir dize içindeki tüm karakterleri büyük harfe değiştirir. Aşağıdaki örnekte "Hello World!" dizesini sayıya dönüştürür büyük harfe karma durumundan.  
  
 [!code-csharp[Strings.ChangingCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#1)]
 [!code-vb[Strings.ChangingCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#1)]  
  
 Önceki örnekte kültüre duyarlı varsayılan olarak; Geçerli kültür büyük/küçük harf kuralları uygular. Kültüre duyarsız büyük/küçük harf değişikliği gerçekleştirmek için veya belirli bir kültür büyük/küçük harf kuralları uygulamak için kullanmak <xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> yöntemi aşırı yükleme ve bir değeri sağlayın <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> veya <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> belirtilen kültür için temsiledennesnesi*kültür* parametresi. Nasıl kullanılacağını gösteren bir örnek için <xref:System.String.ToUpper%2A> kültüre duyarsız büyük/küçük harf değişikliği yapmak için yöntemi bkz [gerçekleştirme kültüre duyarsız durum değişiklikleri](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="tolower"></a>toLower  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType> Yöntemi önceki yöntemine benzer, ancak bunun yerine bir dize içindeki tüm karakterleri küçük harfe dönüştürür. Aşağıdaki örnekte "Hello World!" dizesini sayıya dönüştürür küçük harfe.  
  
 [!code-csharp[Strings.ChangingCase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#2)]
 [!code-vb[Strings.ChangingCase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#2)]  
  
 Önceki örnekte kültüre duyarlı varsayılan olarak; Geçerli kültür büyük/küçük harf kuralları uygular. Kültüre duyarsız büyük/küçük harf değişikliği gerçekleştirmek için veya belirli bir kültür büyük/küçük harf kuralları uygulamak için kullanmak <xref:System.String.ToLower%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> yöntemi aşırı yükleme ve bir değeri sağlayın <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> veya <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> belirtilen kültür için temsiledennesnesi*kültür* parametresi. Nasıl kullanılacağını gösteren bir örnek için <xref:System.String.ToLower%28System.Globalization.CultureInfo%29> kültüre duyarsız büyük/küçük harf değişikliği yapmak için yöntemi bkz [gerçekleştirme kültüre duyarsız durum değişiklikleri](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="totitlecase"></a>ToTitleCase  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> Büyük harfe her sözcüğün ilk karakteri ve kalan karakterleri küçük harfe dönüştürür. Ancak, tamamen büyük harf sözcükler kısaltmalar olduğu varsayılır ve dönüştürülmez.  
  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> Yöntemi kültüre duyarlı; diğer bir deyişle, belirli bir kültür büyük/küçük harf kuralları kullanır. Yöntemini çağırmak için önce aldığınız <xref:System.Globalization.TextInfo> belirli kültür büyük/küçük harf kuralları temsil eden nesnesi <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> belirli bir kültür özelliği.  
  
 Aşağıdaki örnek, bir dizideki her dize geçirir. <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> yöntemi.  Dizeleri kısaltmalar yanı sıra uygun başlık dizeleri içerir. Dizeleri İngilizce (ABD) kültür büyük/küçük harf kuralları kullanarak ilk harfler büyük dönüştürülür.  
  
 [!code-csharp[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/cs/totitlecase2.cs#1)]
 [!code-vb[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/vb/totitlecase2.vb#1)]  
  
 Kültüre duyarlı olmasına rağmen unutmayın <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> yöntemi incelemeye doğru büyük/küçük harf kuralları sağlamaz. Örneğin, önceki örnekte, yöntem "bir hikayesini iki şehirde" "A hikayesini, iki Şehir" için dönüştürür. Ancak, incelemeye doğru başlık büyük/küçük harf en-US kültürü için "Bir hikayesini iki şehirde." olur  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)  
 [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
