---
title: Tam Olarak Nitelenmiş Tür Adlarını Belirtme
ms.date: 03/14/2018
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
ms.openlocfilehash: 437bbb7a1645c0ab13da33e57c1e70b5ec98984c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398684"
---
# <a name="specifying-fully-qualified-type-names"></a>Tam Olarak Nitelenmiş Tür Adlarını Belirtme
Tür adları çeşitli yansıma işlemleri için geçerli giriş belirtmeniz gerekir. Tam olarak nitelenmiş tür adını bir derleme adı belirtimi, bir ad alanı belirtimi ve tür adı oluşur. Tür adı belirtimleri kullanılan yöntemler tarafından gibi <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, ve <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.  
  
## <a name="grammar-for-type-names"></a>Tür adları için dilbilgisi  
 Dilbilgisi resmi diller sözdizimi tanımlar. Aşağıdaki tabloda, geçerli bir giriş tanımak açıklar sözcük kuralları listeler. Terminal (daha fazla reducible olmayan bu öğeleri) tüm büyük harflerle gösterilir. Terminal dışı (daha fazla reducible bu öğeleri) harf karışık veya tek tırnak içine alınmış dizeler gösterilir, ancak tek tırnak işareti (') sözdizimi bir parçası değil. Dikey çizgi karakterinden (&#124;) alt kurallar sahip kuralları gösterir.  

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
    | ArrayTypeSpec
    | TypeName
    ;

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

## <a name="specifying-special-characters"></a>Özel karakterler belirtme  
 Bir tür adı bir dil kuralları tarafından belirlenen geçerli bir ad tanımlayıcısıdır.  
  
 Ters eğik çizgi kullanın (\\) TANIMLAYICI bir parçası olarak kullanıldığında aşağıdaki belirteçleri ayırmak için çıkış karakteri olarak.  
  
|Belirteç|Açıklama|  
|-----------|-------------|  
|\\,|Derleme ayırıcı.|  
|\\+|İç içe geçmiş tür ayırıcısı.|  
|\\&|Başvuru türü.|  
|\\*|İşaretçi türü.|  
|\\[|Dizi boyut sınırlayıcısı.|  
|\\]|Dizi boyut sınırlayıcısı.|  
|\\.|Yalnızca bir dizi belirtimi dönem kullanılıyorsa bir süre önce ters eğik çizgi kullanın. NamespaceSpec dönemlerini ters eğik çizgi kazanmaz.|  
|\\\|Bir dize olarak değişmez değer gerektiğinde ters eğik çizgi.|  
  
 AssemblyNameSpec dışındaki tüm TypeSpec'te bileşenlerinde alanları ilgili olduğunu unutmayın. AssemblyNameSpec ',' ayırıcıdan önce alanları ilgilidir, ancak ',' ayırıcı sonra boşluklar yok sayılır.  
  
 Yansıma sınıfları, gibi <xref:System.Type.FullName%2A?displayProperty=nameWithType>, böylece döndürülen adını çağrıda kullanılabilir karıştırılmış adını döndürmek <xref:System.Type.GetType%2A>, olarak `MyType.GetType(myType.FullName)`.  
  
 Örneğin, bir tür için tam ad olabilir `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.  
  
 Ad alanı olsaydı `Ozzy.Out+Back`, sonra da artı bir eğik gelmelidir. Aksi takdirde, ayrıştırıcı, iç içe geçmiş ayırıcı olarak yorumlar. Yansıma yayar Bu dize olarak `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.  
  
## <a name="specifying-assembly-names"></a>Derleme adları belirtme  
 Bir derleme adı belirtiminde gerekli en az bilgiyi metinsel (TANIMLAYICI) derlemenin adıdır. Aşağıdaki tabloda açıklandığı şekilde özellik/değer çifti virgülle ayrılmış listesi TANIMLAYICISI izleyebilirsiniz. TANIMLAYICI adlandırma dosya adlandırma kuralları izlemelidir. TANIMLAYICI büyük/küçük harf duyarlıdır.  
  
|Özellik adı|Açıklama|İzin verilen değerler|  
|-------------------|-----------------|----------------------|  
|**Sürüm**|Derleme sürüm numarası|*Major.Minor.Build.Revision*, burada *ana*, *küçük*, *yapı*, ve *düzeltme* 0 arasında tamsayı olan ve 65535 (dahil).|  
|**PublicKey**|Tam ortak anahtar|Onaltılık biçimde tam ortak anahtarın değerini dize. Bir null başvuru belirtin (**hiçbir şey** Visual Basic'te) özel bir derleme açıkça belirtmek için.|  
|**PublicKeyToken**|Ortak anahtar belirteci (tam ortak anahtarı karmasını 8-bayt)|Dize değeri, onaltılık biçimde ortak anahtar belirteci. Bir null başvuru belirtin (**hiçbir şey** Visual Basic'te) özel bir derleme açıkça belirtmek için.|  
|**Kültür**|Derleme kültür|RFC 1766 biçimi veya dilden bağımsız (nonsatellite) derlemeler için "nötr" derlemesinde kültür.|  
|**Özel**|Özel ikili büyük nesne (BLOB). Bu şu anda yalnızca tarafından oluşturulan derlemelerde kullanılır [yerel Görüntü Oluşturucu (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|Yerel Görüntü Oluşturucu aracı tarafından Derleme Önbelleği yüklenen derleme yerel görüntü ve bu nedenle yerel görüntü Önbelleği'yüklenecek olduğunu bildirmek için kullanılan özel bir dize. Bir zap dize olarak da bilinir.|  
  
 Aşağıdaki örnekte gösterildiği bir **AssemblyName** varsayılan kültürü yalnızca adlandırılmış bir derleme için.  
  
```csharp  
com.microsoft.crypto, Culture=""   
```  
  
 Aşağıdaki örnek kültür "tr" kesin adlandırılmış bir derleme tam olarak belirtilen bir başvuru gösterir.  
  
```csharp  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0   
```  
  
 Aşağıdaki her bir kısmen belirtilen örnekler **AssemblyName**, hangi memnun güçlü bir ya da yalnızca adlandırılmış bir derleme.  
  
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
  
 Aşağıdaki her bir kısmen belirtilen örnekler **AssemblyName**, hangi gerekir memnun tarafından kesin adlandırılmış bir derleme.  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0  
```  
  
## <a name="specifying-pointers"></a>İşaretçileri belirtme  
 SimpleTypeSpec * bir yönetilmeyen işaretçi temsil eder. Örneğin, MyType yazmanız için bir işaretçi almak için kullanın `Type.GetType("MyType*")`. Bir işaretçi MyType yazmanız için bir işaretçi almak için `Type.GetType("MyType**")`.  
  
## <a name="specifying-references"></a>Başvuruları belirtme  
 SimpleTypeSpec & Yönetilen işaretçi veya reference temsil eder. Örneğin, MyType yazmanız için bir başvuru almak için kullanın `Type.GetType("MyType &")`. İşaretçileri, başvuru bir düzey sınırlı olduğunu unutmayın.  
  
## <a name="specifying-arrays"></a>Diziler belirtme  
 BNF dilbilgisi ReflectionEmitDimension yalnızca kullanarak alınan tamamlanmamış tür tanımları için geçerlidir. <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>. Tamamlanmamış türü tanımlarının <xref:System.Reflection.Emit.TypeBuilder> kullanılarak oluşturulan nesneler <xref:System.Reflection.Emit?displayProperty=nameWithType> ancak üretileceği <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> çağrılmadıysa. ReflectionDimension, yani tamamlanmış herhangi bir tür tanımı, yüklenmiş bir türü almak için kullanılabilir.  
  
 Diziler, dizi derecesini belirterek yansıma erişilen:  
  
-   `Type.GetType("MyArray[]")` 0 alt sınır olan tek boyutlu dizi alır.  
  
-   `Type.GetType("MyArray[*]")` Bilinmeyen alt sınır olan tek boyutlu dizi alır.  
  
-   `Type.GetType("MyArray[][]")` iki boyutlu bir dizinin dizi alır.  
  
-   `Type.GetType("MyArray[*,*]")` ve `Type.GetType("MyArray[,]")` dikdörtgen iki boyutlu bir dizi Bilinmeyen alt sınırlarını ile alır.  
  
 Bir çalışma zamanı açısından bakıldığında, unutmayın `MyArray[] != MyArray[*]`, ancak çok boyutlu diziler için iki gösterimler eşdeğerdir. Diğer bir deyişle, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` değerlendiren **doğru**.  
  
 İçin **ModuleBuilder.GetType**, `MyArray[0..5]` boyutu 6, daha düşük olan tek boyutlu dizi bağlı 0 gösterir. `MyArray[4…]` Bilinmeyen boyutu ve alt sınır 4 tek boyutlu dizi gösterir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection.AssemblyName>  
 <xref:System.Reflection.Emit.ModuleBuilder>  
 <xref:System.Reflection.Emit.TypeBuilder>  
 <xref:System.Type.FullName%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>  
 [Tür Bilgilerini Görüntüleme](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
