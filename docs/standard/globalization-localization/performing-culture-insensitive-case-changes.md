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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160137"
---
# <a name="performing-culture-insensitive-case-changes"></a>Kültüre Duyarsız Büyük/Küçük Değişikliklerini Gerçekleştirme
<xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>ve <xref:System.Char.ToLower%2A?displayProperty=nameWithType> yöntemleri herhangi bir parametreyi kabul etmediğinden aşırı yüklemeler sağlar. Varsayılan olarak, parametreleri olmayan bu aşırı yüklemeler <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>değerine göre değişiklik yapar. Bu, kültüre göre değişebilen büyük/küçük harfe duyarlı sonuçlar üretir. Büyük/küçük harf duyarlı ya da kültüre duyarsız olmasını isteyip istemediğinizi net hale getirmek için, açıkça bir `culture` parametresi belirtmenizi gerektiren bu yöntemlerin aşırı yüklerini kullanmanız gerekir. Kültüre duyarlı durum değişiklikleri için `culture` parametresi için `CultureInfo.CurrentCulture` belirtin. Kültüre duyarsız büyük/küçük harf değişiklikleri için `culture` parametresi için `CultureInfo.InvariantCulture` belirtin.  
  
 Genellikle, dizeler daha sonra daha kolay arama sağlamak için standart bir büyük harfe dönüştürülür. Dizeler bu şekilde kullanıldığında `culture` parametresi için `CultureInfo.InvariantCulture` belirtmelisiniz, çünkü <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> değeri büyük olasılıkla durumun değiştiği zaman ve aramanın gerçekleştiği zaman arasında değişebilir.  
  
 Bir güvenlik kararı bir durum değişikliği işlemini temel alıyorsa, sonucun `CultureInfo.CurrentCulture`değerinden etkilenmemesini sağlamak için işlem kültüre duyarsız olmalıdır. Kültüre duyarlı dize işlemlerinin nasıl tutarsız sonuçlar üretediğini gösteren bir örnek için, [dizeler kullanmanın En Iyi yöntemleri](../../../docs/standard/base-types/best-practices-strings.md) olan "geçerli kültürü kullanan dize karşılaştırmaları" bölümüne bakın.  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>String.ToUpper ve String.ToLower Yöntemlerini Kullanma  
 Kod netliği için, `String.ToUpper` ve `String.ToLower` yöntemlerinin her zaman açıkça bir `culture` parametresi belirtmenize olanak tanıyan aşırı yüklemeleri kullanmanız önerilir. Örneğin, aşağıdaki kod bir tanımlayıcı araması gerçekleştirir. `key.ToLower` işlemi varsayılan olarak kültüre duyarlıdır, ancak bu davranışın kodu okumasından net değildir.  
  
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
  
 `key.ToLower` işleminin kültüre duyarsız olmasını istiyorsanız, bu durumu değiştirirken `CultureInfo.InvariantCulture` açıkça kullanmak için önceki örneği aşağıdaki şekilde değiştirmelisiniz.  
  
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
 `Char.ToUpper` ve `Char.ToLower` yöntemleri `String.ToUpper` ve `String.ToLower` yöntemleriyle aynı özelliklere sahip olsa da, etkilenen tek kültürler Türkçe (Türkiye) ve Azerbaycan dili (Latin, Azerbaycan). Bunlar tek karakterli büyük/küçük harf farklılığı olan tek iki kültürde. Bu benzersiz durum eşleştirmesi hakkında daha fazla ayrıntı için <xref:System.String> sınıfı konusunun "büyük küçük harf" bölümüne bakın. Kod netliği ve tutarlı sonuçlar sağlamak için, bu yöntemlerin her zaman açıkça bir `culture` parametresi belirtmenize olanak tanıyan aşırı yüklemeleri kullanmanız önerilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
