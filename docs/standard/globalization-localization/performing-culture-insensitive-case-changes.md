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
ms.openlocfilehash: 7b2dee03619e24c5a2845699a06e88abab0c594b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160137"
---
# <a name="performing-culture-insensitive-case-changes"></a>Kültüre Duyarsız Büyük/Küçük Değişikliklerini Gerçekleştirme
, <xref:System.String.ToUpper%2A?displayProperty=nameWithType> <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>ve <xref:System.Char.ToLower%2A?displayProperty=nameWithType> yöntemler herhangi bir parametre kabul etmez aşırı yükleri sağlar. Varsayılan olarak, parametreleri olmayan bu aşırı yükler, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>'nin değerini temel alan büyük/küçük harf değişiklikleri gerçekleştirir. Bu, kültüre göre değişebilen büyük/küçük harf duyarlı sonuçlar üretir. Büyük/küçük harf değişikliklerinin kültüre duyarlı mı yoksa kültüre duyarlı mı olmasını istediğinizi açıklığa kavuşturmak için, `culture` bir parametreyi açıkça belirtmenizi gerektiren bu yöntemlerin aşırı yüklerini kullanmanız gerekir. Kültüre duyarlı servis talebi `CultureInfo.CurrentCulture` değişiklikleri `culture` için parametreyi belirtin. Kültüre duyarlı örnek değişiklikler `CultureInfo.InvariantCulture` için `culture` parametreyi belirtin.  
  
 Genellikle, dizeleri daha sonra daha kolay arama sağlamak için standart bir servis talebi dönüştürülür. Dizeleri bu şekilde kullanıldığında, `CultureInfo.InvariantCulture` `culture` parametre için belirtmeniz gerekir, <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> çünkü değer büyük/küçük harfin değiştirilme süresi ile aramanın oluştuğu saat arasında değişebilir.  
  
 Bir güvenlik kararı bir servis talebi değiştirme işlemine dayanıyorsa, sonucun değerinden etkilenmediğinden emin `CultureInfo.CurrentCulture`olmak için işlem kültüre duyarsız olmalıdır. Kültüre duyarlı dize işlemlerinin tutarsız sonuçlar üretebileceğini gösteren bir örnek için [Dizeleri Kullanmak için En İyi Uygulamalar](../../../docs/standard/base-types/best-practices-strings.md) makalesinin "Geçerli Kültürü Kullanan Dize Karşılaştırmaları" bölümüne bakın.  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>String.ToUpper ve String.ToLower Yöntemlerini Kullanma  
 Kod netliği için, bir `String.ToUpper` `String.ToLower` `culture` parametreyi açıkça belirtmenize olanak tanıyan yöntemlerin ve yöntemlerin her zaman aşırı yüklerini kullanmanız önerilir. Örneğin, aşağıdaki kod tanımlayıcı bir arama gerçekleştirir. İşlem `key.ToLower` varsayılan olarak kültüre duyarlıdır, ancak bu davranış kodu okumaktan net değildir.  
  
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
  
 İşlemin `key.ToLower` kültüre duyarsız olmasını istiyorsanız, servis talebi `CultureInfo.InvariantCulture` değiştirilirken aşağıdaki örneği açıkça kullanmak için aşağıdaki örneği değiştirmeniz gerekir.  
  
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
 Metodlar `Char.ToUpper` `Char.ToLower` ve `String.ToLower` metotlar ile aynı özelliklere sahip olmakla birlikte, etkilenen kültürler sadece Türk (Türkiye) ve Azeri (Latince, Azerbaycan) 'dır. `String.ToUpper` Bunlar tek karakterli kasa farklılıkları olan iki kültürdür. Bu benzersiz servis talebi eşleme hakkında daha fazla bilgi <xref:System.String> için sınıf konusundaki "Kasa" bölümüne bakın. Kod netliği ve tutarlı sonuçlar sağlamak için, bir `culture` parametreyi açıkça belirtmenize olanak tanıyan bu yöntemlerin aşırı yüklerini her zaman kullanmanız önerilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
