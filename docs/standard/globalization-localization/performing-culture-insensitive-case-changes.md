---
title: Kültüre Duyarsız Büyük/Küçük Değişikliklerini Gerçekleştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 844b0edb93b93704c4886495c673dc0496f7ba71
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44035901"
---
# <a name="performing-culture-insensitive-case-changes"></a>Kültüre Duyarsız Büyük/Küçük Değişikliklerini Gerçekleştirme
<xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, Ve <xref:System.Char.ToLower%2A?displayProperty=nameWithType> yöntemleri herhangi bir parametre kabul eden aşırı yükler sağlar. Varsayılan olarak, bu aşırı yüklemeler parametresiz değerine göre servis talebi değişiklikleri gerçekleştirmek <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>. Bu, kültüre göre değişebilen büyük küçük harfe duyarlı sonuçlar üretir. Temizleyin, kültüre duyarlı veya kültüre duyarsız büyük/küçük harf değişikliklerini isteyip istemediğinizi hale getirmek için açıkça belirtmek ihtiyaç duyduğunuz bu yöntemleri aşırı kullanmalısınız bir `culture` parametresi. Kültüre duyarlı büyük/küçük harf değişikliklerini belirtin `CultureInfo.CurrentCulture` için `culture` parametresi. Kültüre duyarsız büyük/küçük harf değişikliklerini belirtin `CultureInfo.InvariantCulture` için `culture` parametresi.  
  
 Genellikle, dizeleri daha kolay aramasını daha sonra etkinleştirmek için bir standart küçük harfe dönüştürülür. Dizeleri bu şekilde kullanıldığında belirtmeniz gerekir `CultureInfo.InvariantCulture` için `culture` parametresi, çünkü değerini <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> durumu değişti zaman arasında arama gerçekleşen zaman değiştirebilir miyim.  
  
 Bir güvenlik kararı bir büyük/küçük harf değiştirme işlemi alıyorsa, işlemi kültüre sonucu değerinden etkilenmemesini sağlamak için duyarlı olmalıdır `CultureInfo.CurrentCulture`. "Dize karşılaştırmaları geçerli kültürü kullanan" bölümüne bakın [kullanarak dizeleri için en iyi](../../../docs/standard/base-types/best-practices-strings.md) kültüre duyarlı dize işlemleri gösteren bir örnek tutarsız sonuçlar üretebileceğini için makalesi.  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>String.ToUpper ve String.ToLower Yöntemlerini Kullanma  
 Kod netliği için her zaman aşırı yüklemesini kullanmanız önerilir `String.ToUpper` ve `String.ToLower` belirtmenize olanak tanıyan yöntemler bir `culture` parametre açıkça. Örneğin, aşağıdaki kod, bir tanımlayıcı arama gerçekleştirir. `key.ToLower` İşlem varsayılan, ancak bu davranış kültüre duyarlı kod okumasını açık değil.  
  
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
  
 İsterseniz `key.ToLower` işlemin kültüre duyarsız, olması için önceki örnekte açıkça kullanacak şekilde değiştirmelisiniz `CultureInfo.InvariantCulture` durum değiştirirken.  
  
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
 Ancak `Char.ToUpper` ve `Char.ToLower` yöntemleri aynı özelliklere sahip `String.ToUpper` ve `String.ToLower` yöntemleri, etkilenen tek bir kültür Türkçe (Türkiye) ve Azerice (Latin, Azerbaycan) verilmiştir. Bu, yalnızca iki kültürler tek karakterli büyük/küçük harf farkları vardır. Bu benzersiz büyük/küçük harf eşleştirme hakkında daha fazla ayrıntı için "Büyük/küçük harf" bölümüne bakın. <xref:System.String> sınıf konusuna. Kod netliği ve tutarlı sonuçlar alınması için her zaman bu yöntemlerin açıkça belirtmenize olanak tanıyan aşırı kullanmanız önerilir bir `culture` parametresi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
