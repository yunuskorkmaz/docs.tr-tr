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
ms.openlocfilehash: 656b82daffc62824ed663ea7080bd6d20cd0dadc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045824"
---
# <a name="specifying-fully-qualified-type-names"></a>Tam nitelikli tür adlarını belirtme

Çeşitli yansıma işlemlerine geçerli giriş sağlamak için tür adları belirtmeniz gerekir. Tam nitelikli tür adı, bir derleme adı belirtimi, bir ad alanı belirtimi ve bir tür adından oluşur. Tür <xref:System.Type.GetType%2A?displayProperty=nameWithType>adı belirtimleri <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> ,<xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, ve<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>gibi yöntemler tarafından kullanılır.

## <a name="grammar-for-type-names"></a>Tür adları için dilbilgisi

 Dilbilgisi, biçimsel dillerin sözdizimini tanımlar. Aşağıdaki tabloda, geçerli bir girişin nasıl tanınacağını betimleyen sözlü kurallar listelenmektedir. Terminaller (daha fazla indirgenmiş olmayan öğeler) tüm büyük harflerle gösterilir. Nonterminaller (daha fazla indirgenmiş olan bu öğeler), karışık büyük/küçük ve listedir tırnak içinde gösterilir, ancak tek tırnak (') sözdiziminin kendisinin bir parçası değildir. Kanal karakteri (&#124;), alt kuralların bulunduğu kuralları gösterir.

<!-- markdownlint-disable MD010 -->
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
<!-- markdownlint-enable MD010 -->

## <a name="specifying-special-characters"></a>Özel karakterler belirtme

Tür adında, tanımlayıcı, bir dilin kuralları tarafından belirlenen geçerli bir addır.

Tanımlayıcının bir parçası olarak\\kullanıldığında aşağıdaki belirteçleri ayırmak için bir kaçış karakteri olarak ters eğik çizgi () kullanın.

|Belirteç|Açıklama|
|-----------|-------------|
|\\,|Derleme ayırıcısı.|
|\\+|İç içe tür ayırıcısı.|
|\\&|Başvuru türü.|
|\\*|İşaretçi türü.|
|\\[|Dizi boyut sınırlayıcısı.|
|\\]|Dizi boyut sınırlayıcısı.|
|\\.|Yalnızca nokta bir dizi belirtiminde kullanılıyorsa, bir dönemden önce ters eğik çizgiyi kullanın. NamespaceSpec içindeki dönemler ters eğik çizgi almaz.|
|\\\|Dize sabit değeri olarak gerektiğinde ters eğik çizgi.|

AssemblyNameSpec hariç tüm TypeSpec bileşenlerinde, boşluklar ilgili olduğunu unutmayın. AssemblyNameSpec içinde, ', ' ayırıcısından önceki boşluklar ilgilidir, ancak ', ' ayırıcısından sonra boşluklar yok sayılır.

Gibi yansıma sınıfları <xref:System.Type.FullName%2A?displayProperty=nameWithType>, döndürülen adın ' de `MyType.GetType(myType.FullName)`olduğu gibi bir çağrısında kullanılabilmesi için <xref:System.Type.GetType%2A>karıştırılmış adı döndürür.

Örneğin, bir türün `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`tam nitelikli adı olabilir.

Ad alanı olsaydı `Ozzy.Out+Back`, artı işaretinin önünde ters eğik çizgi gelmelidir. Aksi takdirde, ayrıştırıcı bunu iç içe ayırıcı olarak yorumlar. Yansıma bu dizeyi olarak `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`yayar.

## <a name="specifying-assembly-names"></a>Derleme adlarını belirtme

Bir derleme adı belirtiminde gereken en düşük bilgiler, derlemenin metinsel adıdır (tanımlayıcı). Aşağıdaki tabloda açıklandığı gibi, TANıMLAYıCıYı, bir özellik/değer çiftleri için virgülle ayrılmış bir liste ile takip edebilirsiniz. TANıMLAYıCı adlandırması dosya adlandırmayla ilgili kurallara uymalıdır. TANıMLAYıCı büyük/küçük harfe duyarsızdır.

|Özellik adı|Açıklama|İzin verilen değerler|
|-------------------|-----------------|----------------------|
|**Sürüm**|Derleme sürüm numarası|*Birincil. Minor. Build. Revision*, burada *büyük*, *küçük*, *derleme*ve *Düzeltme* , 0 ile 65535 dahil olmak üzere tamsayılar.|
|**PublicKey**|Tam ortak anahtar|Onaltılık biçimdeki tam ortak anahtarın dize değeri. Özel bir derlemeyi açıkça belirtmek için bir null başvurusu (Visual Basic**hiçbir şey** ) belirtin.|
|**PublicKeyToken**|Ortak anahtar belirteci (tam ortak anahtarın 8 baytlık karması)|Onaltılık biçimdeki ortak anahtar belirtecinin dize değeri. Özel bir derlemeyi açıkça belirtmek için bir null başvurusu (Visual Basic**hiçbir şey** ) belirtin.|
|**Ayarı**|Derleme kültürü|RFC-1766 biçiminde derlemenin kültürü veya dilden bağımsız (uydu olmayan) derlemeler için "nötr".|
|**Özel**|Özel ikili büyük nesne (BLOB). Bu, şu anda yalnızca [Yerel Görüntü Oluşturucu (NGen)](../tools/ngen-exe-native-image-generator.md)tarafından oluşturulan derlemelerde kullanılmaktadır.|Yerel Görüntü Oluşturucu aracı tarafından, yüklenen derlemenin yerel görüntü olduğunu ve bu nedenle yerel görüntü önbelleğine yükleneceğini bildiren derleme önbelleğine bildirmek için kullanılan özel dize. Ayrıca, Zap dizesi olarak da bilinir.|

Aşağıdaki örnek, varsayılan kültür ile basitçe adlandırılmış bir derleme için bir **AssemblyName** gösterir.

```csharp
com.microsoft.crypto, Culture=""
```

Aşağıdaki örnek, "en" kültürü ile kesin adlandırılmış derleme için tam olarak belirtilen başvuruyu gösterir.

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

Aşağıdaki örneklerde her biri, kesin olarak belirtilen bir **AssemblyName**gösterir, bu, güçlü veya basitçe adlandırılmış bir derleme tarafından karşılanır.

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

Aşağıdaki örneklerde, tek bir adlandırılmış derleme tarafından karşılanması gereken kısmen belirtilen **AssemblyName**gösterilmektedir.

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

Aşağıdaki örneklerde her biri, kesin olarak adlandırılmış bir derleme tarafından karşılanması gereken kısmen belirtilen bir **AssemblyName**gösterir.

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

## <a name="specifying-generic-types"></a>Genel türleri belirtme

SimpleTypeSpec\`numarası, 1 ile *n* genel tür parametrelerinden oluşan açık bir genel türü temsil eder. Örneğin, açık genel tür listesi\<T > veya kapalı genel tür listesi\<dize > başvuru almak için, genel tür sözlüğü\<TKey ``Type.GetType("System.Collections.Generic.List`1")`` , TValue > ``Type.GetType("System.Collections.Generic.Dictionary`2")``başvurusunu almak için kullanın.

## <a name="specifying-pointers"></a>İşaretçileri belirtme

SimpleTypeSpec *, yönetilmeyen bir işaretçiyi temsil eder. Örneğin, MyType türünde bir işaretçi almak için kullanın `Type.GetType("MyType*")`. MyType türünde bir işaretçiye işaretçi almak için kullanın `Type.GetType("MyType**")`.

## <a name="specifying-references"></a>Başvuruları belirtme

SimpleTypeSpec &, yönetilen bir işaretçiyi veya başvuruyu temsil eder. Örneğin, MyType türü için bir başvuru almak için kullanın `Type.GetType("MyType &")`. İşaretçilerin aksine, başvuruların bir düzey ile sınırlı olduğunu unutmayın.

## <a name="specifying-arrays"></a>Dizileri belirtme

BNF dilbilgisinde, ReflectionEmitDimension yalnızca kullanılarak <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>alınan eksik tür tanımları için geçerlidir. Tamamlanmamış tür tanımları <xref:System.Reflection.Emit.TypeBuilder> kullanılarak <xref:System.Reflection.Emit?displayProperty=nameWithType> oluşturulan, ancak üzerinde <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> olmayan nesneler. ReflectionDimension, tamamlanmış olan ve yüklenmiş bir tür tanımını almak için kullanılabilir.

Dizilere dizi derecesi belirtilerek bir şekilde erişilir:

- `Type.GetType("MyArray[]")`0 alt sınırı olan tek boyutlu bir diziyi alır.

- `Type.GetType("MyArray[*]")`bilinmeyen alt sınır içeren tek boyutlu bir dizi alır.
- `Type.GetType("MyArray[][]")`iki boyutlu bir dizinin dizisini alır.

- `Type.GetType("MyArray[*,*]")`ve `Type.GetType("MyArray[,]")` bilinmeyen alt sınırlara sahip dikdörtgen iki boyutlu bir dizi alır.

Bir çalışma zamanı noktasından, ancak çok boyutlu diziler `MyArray[] != MyArray[*]`için iki gösterimin eşdeğer olduğunu unutmayın. Yani, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` **true**olarak değerlendirilir.

**ModuleBuilder. GetType**için, `MyArray[0..5]` 6 boyutunda bir tek boyutlu diziyi, alt sınır 0 ' ı gösterir. `MyArray[4…]`Bilinmeyen boyut ve alt sınır 4 ' ün tek boyutlu dizisini gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [Tür Bilgilerini Görüntüleme](viewing-type-information.md)
