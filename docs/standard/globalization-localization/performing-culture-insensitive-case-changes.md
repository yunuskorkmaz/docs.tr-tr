---
title: "Kültüre Duyarsız Büyük/Küçük Değişikliklerini Gerçekleştirme"
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
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c500b882c335572b8b458ba515b282e9f5362b85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-case-changes"></a>Kültüre Duyarsız Büyük/Küçük Değişikliklerini Gerçekleştirme
<xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, Ve <xref:System.Char.ToLower%2A?displayProperty=nameWithType> herhangi bir parametre kabul ediyor musunuz aşırı yöntemleri sağlar. Varsayılan olarak, bu aşırı parametresiz değerine göre durum değişiklikleri gerçekleştirmek <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>. Kültür göre değişebilir büyük küçük harfe duyarlı sonuçlar üretir. Clear kültüre duyarlı veya kültüre duyarsız büyük/küçük değişikliklerini istediğinizi yapmak için açıkça belirtmek ihtiyaç duyduğunuz bu yöntemlerin aşırı kullanmalısınız bir `culture` parametresi. Kültüre duyarlı durum değişiklikleri belirtin `CultureInfo.CurrentCulture` için `culture` parametresi. Kültüre duyarsız büyük/küçük değişikliklerini belirtin `CultureInfo.InvariantCulture` için `culture` parametresi.  
  
 Genellikle, dizeleri daha sonra daha kolay aramasını etkinleştirmek için standart talebine dönüştürülür. Dizeleri bu şekilde kullanıldığında belirtmeniz gerekir `CultureInfo.InvariantCulture` için `culture` parametresi, çünkü değerini <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> durumu değişti zaman ve arama oluşur saat arasında potansiyel olarak değiştirebilirsiniz.  
  
 Güvenlik kararı bir büyük/küçük harf değiştirme işlemi temel alıyorsa, işlemi kültüre sonuç değeri olarak etkilenmediğinden emin olmak için duyarsız olmalıdır `CultureInfo.CurrentCulture`. "Dize karşılaştırmaları kullanma geçerli kültür" bölümüne bakın [kullanarak dizeleri için en iyi uygulamaları](../../../docs/standard/base-types/best-practices-strings.md) nasıl kültüre duyarlı dize işlemleri gösteren bir örnek tutarsız sonuçlara yol açabilir için makalesi.  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>String.ToUpper ve String.ToLower Yöntemlerini Kullanma  
 Kodu daha anlaşılır olması için her zaman aşırı kullanmanız önerilir `String.ToUpper` ve `String.ToLower` belirtmenize olanak veren yöntemler bir `culture` parametre açıkça. Örneğin, aşağıdaki kod bir tanımlayıcı araması gerçekleştirir. `key.ToLower` İşlemi kültüre duyarlı varsayılan, ancak bu davranış kodu okuma açık değil.  
  
### <a name="example"></a>Örnek  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 İstiyorsanız, `key.ToLower` kültüre duyarsız, olmasını işlemi aşağıdaki gibi açıkça kullanmak için önceki örnekte değiştirmelisiniz `CultureInfo.InvariantCulture` durum değiştirirken.  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a>Char.ToUpper ve Char.ToLower Yöntemlerini Kullanma  
 Ancak `Char.ToUpper` ve `Char.ToLower` yöntemleri aynı özelliklere sahip `String.ToUpper` ve `String.ToLower` yöntemleri, etkilenen yalnızca kültürler: Türkçe (Türkiye) ve Azerice (Latin, Azerbaycan). Yalnızca iki kültürler tek-büyük farklılıklar şunlardır. Bu benzersiz servis talebi eşleştirme hakkında daha fazla ayrıntı için "Büyük" bölümüne bakın <xref:System.String> sınıfı konu. Kodu daha anlaşılır olması ve tutarlı sonuçlar alınması aşırı açıkça belirtmenize olanak veren bu yöntemlerin her zaman kullanmanız önerilir bir `culture` parametresi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
 [Kültüre duyarsız dize işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
