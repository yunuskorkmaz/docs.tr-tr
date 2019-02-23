---
title: Tam Olarak Nitelenmiş Tür Adlarını Belirtme
ms.date: 02/21/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- languages, grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d73cad94e0e4343c5dd09a3b12131afeabef873
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747255"
---
# <a name="specifying-fully-qualified-type-names"></a>Tam olarak nitelenmiş tür adlarını belirtme
Çeşitli yansıma işlemleri için geçerli bir giriş için tür adları belirtmeniz gerekir. Bir derleme adı belirtimi, bir ad alanı belirtimine ve bir tür adı tam olarak nitelenmiş tür adını içerir. Tür adı belirtimleri kullanılan yöntemleri tarafından gibi <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, ve <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.  
  
## <a name="grammar-for-type-names"></a>Tür adları için dil bilgisi  
 Dilbilgisi biçimsel dillerin sözdizimi tanımlar. Aşağıdaki tabloda, geçerli bir giriş anlamayı açıklayan sözcük temelli kurallar listelenmektedir. Tüm büyük harfleri terminaller (daha fazla reducible olmayan bu öğeleri) gösterilmektedir. Terminal olmayanları (daha fazla reducible bu öğeleri) karışık veya tek tırnak içine alınmış dizeler gösterilir, ancak tek tırnak (') sözdizimi bir parçası değil. Dikey çizgi karakterinden (&#124;) alt olan kuralları gösterir.  

```antlr
TypeSpec
    : ReferenceTypeSpec
    | SimpleTypeSpec
    ;

ReferenceTypeSpec
    : SimpleTypeSpec '&'
    ;

SimpleTypeSpec
    : PointerTypeSpec
    | GenericTypeSpec
    | TypeName
    ;

GenericTypeSpec
   : SimpleTypeSpec ` NUMBER

PointerTypeSpec
    : SimpleTypeSpec '*'
    ;

ArrayTypeSpec
    : SimpleTypeSpec '[ReflectionDimension]'
    | SimpleTypeSpec '[ReflectionEmitDimension]'
    ;

ReflectionDimension
    : '*'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

ReflectionEmitDimension
    : '*'
    | Number '..' Number
    | Number '…'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

Number
    : [0-9]+
    ;

TypeName
    : NamespaceTypeName
    | NamespaceTypeName ',' AssemblyNameSpec
    ;

NamespaceTypeName
    : NestedTypeName
    | NamespaceSpec '.' NestedTypeName
    ;

NestedTypeName
    : IDENTIFIER
    | NestedTypeName '+' IDENTIFIER
    ;

NamespaceSpec
    : IDENTIFIER
    | NamespaceSpec '.' IDENTIFIER
    ;

AssemblyNameSpec
    : IDENTIFIER
    | IDENTIFIER ',' AssemblyProperties
    ;

AssemblyProperties
    : AssemblyProperty
    | AssemblyProperties ',' AssemblyProperty
    ;

AssemblyProperty
    : AssemblyPropertyName '=' AssemblyPropertyValue
    ;
```

## <a name="specifying-special-characters"></a>Özel karakter belirtme  
 Bir tür adı bir dil kuralları tarafından belirlenen geçerli bir ad tanımlayıcısıdır.  
  
 Ters eğik çizgi kullanın (\\) olarak TANIMLAYICI bir parçası olarak kullanıldığında aşağıdaki belirteçler ayırmak için bir kaçış karakteri.  
  
|Belirteç|Açıklama|  
|-----------|-------------|  
|\\,|Derleme ayırıcı.|  
|\\+|İç içe geçmiş tür ayırıcı.|  
|\\&|Başvuru türü.|  
|\\*|İşaretçi türü.|  
|\\[|Dizi boyut sınırlayıcısı.|  
|\\]|Dizi boyut sınırlayıcısı.|  
|\\.|Yalnızca nokta bir dizi belirtiminde kullanılıyorsa bir süre önce ters eğik çizgi kullanın. Ters eğik çizgi NamespaceSpec dönemlerde almaz.|  
|\\\|Değişmez değer dize olarak gerektiğinde ters eğik çizgi.|  
  
 Alanları AssemblyNameSpec dışındaki tüm TypeSpec'te bileşenlerinde ilgili olduğunu unutmayın. AssemblyNameSpec ',' ayırıcısından önceki boşluklar ilgilidir, ancak ',' ayırıcısından sonraki boşluklar yok sayılır.  
  
 Yansıma sınıfları, gibi <xref:System.Type.FullName%2A?displayProperty=nameWithType>, böylece bir çağrıda döndürülen adını kullanılabilir karıştırılmış adını döndürmek <xref:System.Type.GetType%2A>, olarak `MyType.GetType(myType.FullName)`.  
  
 Örneğin, bir tür için tam ad olabilir `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.  
  
 Ad alanı varsa `Ozzy.Out+Back`, ardından artı işaretine bir ters eğik çizgi gelmelidir. Aksi takdirde, ayrıştırıcının, iç içe geçmiş bir ayırıcı olarak yorumlar. Yansıma Bu dize olarak yayar `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.  
  
## <a name="specifying-assembly-names"></a>Derleme adları belirtme  
 Bir derleme adı belirtimi gereken en düşük bilgileri metinsel (TANIMLAYICI) derlemenin adıdır. Aşağıdaki tabloda açıklandığı gibi özellik/değer çiftlerinin virgülle ayrılmış bir listesini, TANIMLAYICI takip edebilirsiniz. TANIMLAYICI adlandırma dosya adlandırma kuralları izlemelidir. TANIMLAYICI büyük/küçük harf duyarlıdır.  
  
|Özellik adı|Açıklama|İzin verilen değerler|  
|-------------------|-----------------|----------------------|  
|**Sürüm**|Derleme sürüm numarası|*Major.Minor.Build.Revision*burada *ana*, *küçük*, *derleme*, ve *düzeltme* 0 arasındaki tam sayılardır ve 65535 (dahil).|  
|**PublicKey**|Tam ortak anahtarı|Onaltılık biçimde tam ortak anahtar dizesi. Bir null başvurusu belirtin (**hiçbir şey** Visual Basic'te) özel bir derleme açıkça belirtmek için.|  
|**PublicKeyToken**|Ortak anahtar belirteci (8 baytlık tam ortak anahtar karması)|Onaltılık biçiminde ortak anahtar belirteci dizesi. Bir null başvurusu belirtin (**hiçbir şey** Visual Basic'te) özel bir derleme açıkça belirtmek için.|  
|**Kültür**|Derleme kültürü|RFC 1766 biçimi veya "belirsiz" dilden bağımsız (nonsatellite) derlemeler için derleme kültür.|  
|**Özel**|Özel ikili büyük nesne (BLOB). Bu şu anda yalnızca tarafından oluşturulan bütünleştirilmiş kodlarında kullanılır [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|Yerel Görüntü Oluşturucu aracı tarafından derleme önbelleğine yüklenen derleme bir doğal görüntü ve bu nedenle yerel görüntü önbelleğine yüklenecek olduğunu bildirmek için kullanılan özel bir dize. Zap dize olarak da adlandırılır.|  
  
 Aşağıdaki örnekte gösterildiği bir **AssemblyName** varsayılan kültür ile yalnızca adlandırılmış bir derleme için.  
  
```csharp  
com.microsoft.crypto, Culture=""   
```  
  
 Aşağıdaki örnek, "en" kültürüyle kesin adlandırılmış bir bütünleştirilmiş kod için tam olarak belirtilen bir başvuru gösterir.  
  
```csharp  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0   
```  
  
 Aşağıdaki her bir kısmen belirtilen örnekler **AssemblyName**, hangi memnun güçlü veya yalnızca adlandırılmış bir bütünleştirilmiş kod tarafından.  
  
```csharp  
com.microsoft.crypto  
com.microsoft.crypto, Culture=""  
com.microsoft.crypto, Culture=en   
```  
  
 Aşağıdaki her bir kısmen belirtilen örnekler **AssemblyName**, hangi gerekir memnun tarafından yalnızca adlandırılmış bir derleme.  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=null   
com.microsoft.crypto, Culture=en, PublicKeyToken=null  
```  
  
 Aşağıdaki her bir kısmen belirtilen örnekler **AssemblyName**, hangi gerekir memnun kesin adlandırılmış bir derleme tarafından.  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0  
```  
## <a name="specifying-generic-types"></a>Genel türleri belirtme

SimpleTypeSpec\`SAYIYI temsil eden bir açık genel tür ile 1'den *n* genel tür parametreleri. Örneğin, başvuru açık genel tür listesini almak için\<T > ya da kapalı genel tür listesi\<dizesi >, kullanın ``Type.GetType("System.Collections.Generic.List`1")`` genel tür sözlük için bir başvuru almak için\<TKey, TValue >, kullanın ``Type.GetType("System.Collections.Generic.Dictionary`2")``. 

## <a name="specifying-pointers"></a>İşaretçileri belirtme  
 SimpleTypeSpec * bir yönetilmeyen işaretçi temsil eder. Örneğin, MyType tür işaretçisi almak için kullanın `Type.GetType("MyType*")`. MyType tür işaretçisi için bir işaretçi almak için kullanın `Type.GetType("MyType**")`.  
  
## <a name="specifying-references"></a>Başvuruları belirtme  
 SimpleTypeSpec & bir yönetilen işaretçi veya başvuru temsil eder. Örneğin, MyType yazmanız için bir başvuru almak için kullanın `Type.GetType("MyType &")`. İşaretçilerin, başvuru bir düzey sınırlı olduğunu unutmayın.  
  
## <a name="specifying-arrays"></a>Diziler belirtme  
 BNF dilbilgisi ReflectionEmitDimension eksik tür tanımlarını kullanarak yalnızca geçerli <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>. Eksik tür tanımları <xref:System.Reflection.Emit.TypeBuilder> kullanılarak oluşturulan nesneleri <xref:System.Reflection.Emit?displayProperty=nameWithType> ancak üretileceği <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> çağrılmadıysa. ReflectionDimension, yani tamamlanmış olan herhangi bir tür tanımı, yüklenmiş olan bir tür almak için kullanılabilir.  
  
 Diziler, dizi boyut sayısını belirterek yansıma erişilir:  
  
-   `Type.GetType("MyArray[]")` bir tek boyutlu dizi alt sınırı 0 ile alır.  
  
-   `Type.GetType("MyArray[*]")` Bilinmeyen alt sınır olan bir tek boyutlu dizi alır.  
-   `Type.GetType("MyArray[][]")` iki boyutlu bir dizinin dizisini alır.  
  
-   `Type.GetType("MyArray[*,*]")` ve `Type.GetType("MyArray[,]")` dikdörtgen iki boyutlu bir dizi ile Bilinmeyen alt sınırını alır.  
  
 Bir çalışma zamanı açısından bakıldığında, dikkat `MyArray[] != MyArray[*]`, ancak çok boyutlu diziler için iki gösterimler eşdeğerdir. Diğer bir deyişle, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` değerlendiren **true**.  
  
 İçin **ModuleBuilder.GetType**, `MyArray[0..5]` bir tek boyutlu dizi boyutu 6, daha düşük ile bağlı 0 gösterir. `MyArray[4…]` bir tek boyutlu dizi boyutu bilinmeyen ve alt sınırı 4 gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [Tür Bilgilerini Görüntüleme](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
