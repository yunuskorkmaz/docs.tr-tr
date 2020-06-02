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
ms.openlocfilehash: 6baef7b0a5bbdacd33d84df01b1aa943897a9e3d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276822"
---
# <a name="performing-culture-insensitive-case-changes"></a>Kültüre Duyarsız Büyük/Küçük Değişikliklerini Gerçekleştirme
<xref:System.String.ToUpper%2A?displayProperty=nameWithType>,, <xref:System.String.ToLower%2A?displayProperty=nameWithType> <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> Ve <xref:System.Char.ToLower%2A?displayProperty=nameWithType> yöntemleri herhangi bir parametreyi kabul etmayan aşırı yüklemeler sağlar. Varsayılan olarak, parametreleri olmayan bu aşırı yüklemeler, değerine göre değişiklik yapar <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> . Bu, kültüre göre değişebilen büyük/küçük harfe duyarlı sonuçlar üretir. Büyük/küçük harf duyarlı ya da kültüre duyarsız olmasını isteyip istemediğinizi net hale getirmek için, açıkça bir parametre belirtmenizi gerektiren bu yöntemlerin aşırı yüklerini kullanmanız gerekir `culture` . Kültüre duyarlı durum değişiklikleri için `CultureInfo.CurrentCulture` parametresi için öğesini belirtin `culture` . Kültüre duyarsız büyük/küçük harf değişiklikleri için `CultureInfo.InvariantCulture` parametresi için öğesini belirtin `culture` .  
  
 Genellikle, dizeler daha sonra daha kolay arama sağlamak için standart bir büyük harfe dönüştürülür. Dizeler bu şekilde kullanıldığında parametresini belirtmeniz gerekir `CultureInfo.InvariantCulture` `culture` , çünkü değeri <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> büyük olasılıkla durumun değiştiği zaman ve aramanın gerçekleştiği zaman arasında değişebilir.  
  
 Bir güvenlik kararı bir durum değişikliği işlemini temel alıyorsa, sonucun değerinden etkilenmemesini sağlamak için işlem kültür duyarsız olmalıdır `CultureInfo.CurrentCulture` . Kültüre duyarlı dize işlemlerinin nasıl tutarsız sonuçlar üretediğini gösteren bir örnek için, [dizeler kullanmanın En Iyi yöntemleri](../base-types/best-practices-strings.md) olan "geçerli kültürü kullanan dize karşılaştırmaları" bölümüne bakın.  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>String.ToUpper ve String.ToLower Yöntemlerini Kullanma  
 Kod netliği için, `String.ToUpper` ve yöntemlerinin her zaman `String.ToLower` açıkça bir parametre belirtmenizi sağlayan aşırı yüklerini kullanmanız önerilir `culture` . Örneğin, aşağıdaki kod bir tanımlayıcı araması gerçekleştirir. `key.ToLower`İşlem varsayılan olarak kültüre duyarlıdır, ancak bu davranışın kodu okumasından net değildir.  
  
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
  
 `key.ToLower`İşlemin kültüre duyarsız olmasını istiyorsanız, önceki örneği aşağıdaki şekilde değiştirmeniz gerekir ve bu `CultureInfo.InvariantCulture` durumda, servis talebi değiştirirken açık bir şekilde kullanılır.  
  
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
 `Char.ToUpper`Ve `Char.ToLower` yöntemleri ve yöntemleriyle aynı özelliklere sahip olsa da `String.ToUpper` `String.ToLower` , etkilenen tek kültürler Türkçe (Türkiye) ve Azerbaycan dili (Latin, Azerbaycan). Bunlar tek karakterli büyük/küçük harf farklılığı olan tek iki kültürde. Bu benzersiz durum eşleştirmesi hakkında daha fazla ayrıntı için, sınıf konusunun "büyük küçük harf" bölümüne bakın <xref:System.String> . Kod netliği ve tutarlı sonuçlar sağlamak için, bu yöntemlerin her zaman açıkça bir parametre belirtmenize olanak tanıyan aşırı yüklemeleri kullanmanız önerilir `culture` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](performing-culture-insensitive-string-operations.md)
