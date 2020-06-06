---
title: Yansıma kullanan API'ler
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
ms.openlocfilehash: 1d8daceb6b744b984f86b011ad7952d0da583a79
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181087"
---
# <a name="apis-that-rely-on-reflection"></a>Yansıma kullanan API'ler
Bazı durumlarda, kodda yansıma kullanımı belirgin değildir ve bu nedenle .NET Native araç zinciri çalışma zamanında gereken meta verileri korumaz. Bu konu, yansıma API 'sinin bir parçası olarak kabul edilmeyen ancak yansıma dosyasını başarıyla yürütmek için kullanan bazı ortak API 'Leri veya ortak programlama düzenlerini ele almaktadır. Bunları kaynak kodunuzda kullanıyorsanız, bu API 'lere yapılan çağrıların bir [MissingMetadataException](missingmetadataexception-class-net-native.md) özel durumu veya çalışma zamanında başka bir özel durum oluşturmaması için çalışma zamanı yönergeleri (. RD. xml) dosyasına bunlarla ilgili bilgi ekleyebilirsiniz.  
  
## <a name="typemakegenerictype-method"></a>Type. MakeGenericType yöntemi  
 `AppClass<T>` <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> Aşağıdaki gibi bir kod kullanarak yöntemini çağırarak bir genel türü dinamik olarak oluşturabilirsiniz:  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 Bu kodun çalışma zamanında başarılı olması için birkaç meta veri öğesi gereklidir. İlki, `Browse` örneklenmemiş genel türün meta verilerdir `AppClass<T>` :  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 Bu <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> yöntem çağrısının başarılı olmasını ve geçerli bir nesne döndürmesini sağlar <xref:System.Type> .  
  
 Ancak, örneklenmemiş genel tür için meta veriler eklediğinizde bile <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> yöntemi çağırmak bir [MissingMetadataException](missingmetadataexception-class-net-native.md) özel durumu oluşturur:  
  
Bu işlem, performans nedenleriyle aşağıdaki tür için meta veriler kaldırıldığından yürütülemiyor:  
  
`App1.AppClass`1<System. Int32>'.  
  
 `Activate`Belirli bir örnek oluşturma için meta verileri eklemek üzere çalışma zamanı yönergeleri dosyasına aşağıdaki çalışma zamanı yönergesini ekleyebilirsiniz `AppClass<T>` <xref:System.Int32?displayProperty=nameWithType> :  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"
                   Activate="Required Public" />  
```  
  
 Her farklı örnekleme `AppClass<T>` , yöntemiyle oluşturulduysa ve statik olarak kullanılmazsa ayrı bir yönerge gerektirir <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> .  
  
## <a name="methodinfomakegenericmethod-method"></a>MethodInfo. MakeGenericMethod yöntemi  
 `Class1`Genel bir yöntemi olan bir sınıf verildiğinde `GetMethod<T>(T t)` , aşağıdaki gibi bir `GetMethod` kod kullanılarak yansıma aracılığıyla çağrılabilir:  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 Başarılı bir şekilde çalıştırmak için, bu kod birçok meta veri öğesi gerektirir:  
  
- `Browse`yöntemi çağırmak istediğiniz türün meta verileri.  
  
- `Browse`çağırmak istediğiniz metodun meta verileri.  Ortak bir yöntem ise, `Browse` kapsayan tür için ortak meta verileri eklemek de yöntemini içerir.  
  
- Çağırmak istediğiniz metodun dinamik meta verileri, böylece yansıma çağırma temsilcisi .NET Native araç zinciri tarafından kaldırılmaz. Yöntemi için dinamik meta veriler eksikse, yöntemi çağrıldığında aşağıdaki özel durum oluşur <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> :  
  
    ```output
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 Aşağıdaki çalışma zamanı yönergeleri tüm gerekli meta verilerin kullanılabilir olduğundan emin olur:  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 `MethodInstantiation`Dinamik olarak çağrılan metodun her farklı örneklemesi için bir yönerge gereklidir ve `Arguments` öğe, her farklı örnekleme bağımsız değişkenini yansıtacak şekilde güncelleştirilir.  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a>Array. CreateInstance ve Type. MakeTypeArray yöntemleri  
 Aşağıdaki örnek, <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> ve <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> yöntemlerini bir tür üzerinde çağırır `Class1` .  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 Hiçbir dizi meta verisi yoksa, aşağıdaki hata oluşur:  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 `Browse`dizi türü için meta veriler dinamik olarak örneğini oluşturmak için gereklidir.  Aşağıdaki çalışma zamanı yönergesi dinamik örneklemeyi sağlar `Class1[]` .  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](getting-started-with-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
