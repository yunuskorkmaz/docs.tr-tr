---
title: Yansıma kullanan API'ler
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
ms.openlocfilehash: 1d8daceb6b744b984f86b011ad7952d0da583a79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181087"
---
# <a name="apis-that-rely-on-reflection"></a>Yansıma kullanan API'ler
Bazı durumlarda, koddaki yansımakullanımı açık değildir ve bu nedenle .NET Native araç zinciri çalışma zamanında gereken meta verileri korumaz. Bu konu, yansıma API'sinin bir parçası olarak kabul edilen ancak başarılı bir şekilde yürütmek için yansımaya dayanan bazı yaygın API'leri veya ortak programlama desenlerini kapsar. Bunları kaynak kodunuzda kullanırsanız, bu API'lere yapılan çağrıların çalışma zamanında [Eksik MetadataException](missingmetadataexception-class-net-native.md) özel durumu veya başka bir özel durum atmaması için çalışma zamanı yönergeleri (.rd.xml) dosyasına bunlarla ilgili bilgileri ekleyebilirsiniz.  
  
## <a name="typemakegenerictype-method"></a>Type.MakeGenericType yöntemi  
 Aşağıdaki gibi bir kod kullanarak `AppClass<T>` <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> yöntemi arayarak genel bir türü dinamik olarak anında atabilirsiniz:  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 Bu kodun çalışma zamanında başarılı olması için çeşitli meta veri öğeleri gereklidir. İlk anlık `Browse` olmayan genel türü için meta veri, `AppClass<T>`:  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 Bu <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> yöntem arama başarılı ve geçerli <xref:System.Type> bir nesne döndürmesağlar.  
  
 Ancak, anlık olmayan genel tür için meta veri eklediğinizde <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> bile, yöntemi çağırmak [Bir EksikMetadataException](missingmetadataexception-class-net-native.md) özel durum atar:  
  
Bu işlem, performans nedenleriyle aşağıdaki türiçin meta veri kaldırıldığı ndan yürütülemez:  
  
`App1.AppClass`1<System.Int32>'.  
  
 Aşağıdaki çalışma zamanı yönergeleri dosyasına aşağıdaki anlık `Activate` `AppClass<T>` veriler için meta veri <xref:System.Int32?displayProperty=nameWithType>ekleyebilirsiniz:  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"
                   Activate="Required Public" />  
```  
  
 Üzerinde her farklı `AppClass<T>` anlık yöntem ile <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> oluşturulan ve statik olarak kullanılmayan ayrı bir yönerge gerektirir.  
  
## <a name="methodinfomakegenericmethod-method"></a>MethodInfo.MakeGenericMethod yöntemi  
 Genel bir `Class1` yönteme `GetMethod<T>(T t)`sahip `GetMethod` bir sınıf göz önüne alındığında, bu gibi kod kullanılarak yansıma yoluyla çağrılabilir:  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 Başarılı bir şekilde çalıştırmak için bu kod birkaç meta veri öğesi gerektirir:  
  
- `Browse`yöntemini çağırmak istediğiniz tür için meta veriler.  
  
- `Browse`aramak istediğiniz yöntem için meta veriler.  Genel bir yöntemse, `Browse` içeren tür için ortak meta veri eklemek de yöntemi içerir.  
  
- Yansıtma çağırma temsilcisinin .NET Yerel araç zinciri tarafından kaldırılmaması için çağırmak istediğiniz yöntem için dinamik meta veriler. Yöntem için dinamik meta veri eksikse, <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> yöntem çağrıldığında aşağıdaki özel durum atılır:  
  
    ```output
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 Aşağıdaki çalışma zamanı yönergeleri, gerekli tüm meta verilerin kullanılabilir olmasını sağlar:  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 Dinamik `MethodInstantiation` olarak çağrılan yöntemin her farklı anlık iletimi için bir `Arguments` yönerge gereklidir ve öğe her farklı anlık değişkeni yansıtacak şekilde güncelleştirilir.  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a>Array.CreateInstance ve Type.MakeTypeArray yöntemleri  
 Aşağıdaki örnek, <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> bir <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> tür ve `Class1`yöntemleri çağırır.  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 Dizi meta verisi yoksa, aşağıdaki hata sonuçları:  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 `Browse`dizi türü için meta veri dinamik olarak anlık olarak gereklidir.  Aşağıdaki çalışma zamanı yönergesi `Class1[]`dinamik instantiation sağlar.  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](getting-started-with-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
