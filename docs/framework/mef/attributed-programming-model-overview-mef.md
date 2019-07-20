---
title: Öznitelikli Programlama Modeline Genel Bakış (MEF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MEF, attributed programming model
- attributed programming model [MEF]
ms.assetid: 49b787ff-2741-4836-ad51-c3017dc592d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bed67019fdd3bb81585d08349715a895dfe5a681
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363953"
---
# <a name="attributed-programming-model-overview-mef"></a>Öznitelikli Programlama Modeline Genel Bakış (MEF)

Managed Extensibility Framework (MEF) içinde, bir *programlama MODELI* MEF 'in üzerinde çalıştığı kavramsal nesneler kümesini tanımlamaya yönelik belirli bir yöntemdir. Bu kavramsal nesneler parçalar, içeri aktarmalar ve dışarı aktarmaları içerir. MEF bu nesneleri kullanır, ancak nasıl temsil edileceğini belirtmez. Bu nedenle, özelleştirilmiş programlama modelleri de dahil olmak üzere çok çeşitli programlama modelleri mümkündür.

MEF 'te kullanılan varsayılan programlama modeli, *öznitelikli programlama modelidir*. Öznitelikli programlama modeli bölümlerinde, içeri aktarmalar, dışarı aktarımlar ve diğer nesneler, sıradan .NET Framework sınıfları süsleten öznitelikler ile tanımlanmıştır. Bu konu başlığı altında, bir MEF uygulaması oluşturmak için Öznitelikli programlama modeli tarafından sunulan özniteliklerin nasıl kullanılacağı açıklanmaktadır.

<a name="import_and_export_basics"></a>

## <a name="import-and-export-basics"></a>İçeri ve dışarı aktarma temelleri

*Dışarı aktarma* , bir bölümün kapsayıcıdaki diğer bölümlere sağladığı bir değerdir ve *içeri aktarma* işlemi, kullanılabilir dışarı aktarımlardan doldurulacak bir bölümün kapsayıcının ifade olduğu gereksinimdir. Öznitelikli programlama modelinde, içeri aktarmalar ve dışarı aktarımlar, `Import` ve `Export` öznitelikleri ile sınıflar veya Üyeler dekorasyon tarafından tanımlanır. Özniteliği bir alanı, özelliği veya Oluşturucu parametresini süslemek için bir sınıfı, alanı, `Import` özelliği veya yöntemi süsedebilir. `Export`

İçeri aktarmanın bir dışarı aktarma işlemiyle eşleşmesi için, içeri ve dışarı aktarmanın aynı *sözleşmeye*sahip olması gerekir. Sözleşme, sözleşme *adı*olarak adlandırılan bir dizeden ve verilen ya da içeri aktarılan nesnenin türü, *anlaşma türü*olarak adlandırılır. Yalnızca anlaşma adı ve anlaşma türü eşleşiyorsa, belirli bir içeri aktarma işlemini yerine getirmek için kabul edilen bir dışarı aktarma işlemi olur.

Anlaşma parametrelerinden biri veya her ikisi örtük veya açık olabilir. Aşağıdaki kod, temel bir içeri aktarma bildiren bir sınıfı gösterir.

```vb
Public Class MyClass1
    <Import()>
    Public Property MyAddin As IMyAddin
End Class
```

```csharp
public class MyClass
{
    [Import]
    public IMyAddin MyAddin { get; set; }
}
```

Bu içeri aktarımda, `Import` öznitelik bir anlaşma türüne veya bir anlaşma adı parametresine bağlı değildir. Bu nedenle, her ikisi de düzenlenmiş özelliğinden çıkarsedilir. Bu durumda, sözleşme türü `IMyAddin`olur ve anlaşma adı Sözleşme türünden oluşturulan benzersiz bir dize olur. (Başka bir deyişle, sözleşme adı yalnızca adları türden `IMyAddin`de çıkarılan dışarı aktarmalar ile eşleşir.)

Aşağıda, önceki içeri aktarma ile eşleşen bir dışarı aktarma gösterilmektedir.

```vb
<Export(GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export(typeof(IMyAddin))]
public class MyLogger : IMyAddin { }
```

Bu dışarı aktarmada, sözleşme türü `IMyAddin` `Export` özniteliğin bir parametresi olarak belirtilmediği için olur. İçe aktarılmış tür, anlaşma türüyle aynı olmalıdır, anlaşma türünden türetilir ya da bir arabirimteise sözleşme türünü uygular. Bu dışa aktarmada gerçek tür `MyLogger` arabirimini `IMyAddin`uygular. Sözleşme adı, Sözleşme türünden algılanır, bu da dışarı aktarmanın önceki içeri aktarma ile eşleşmeyeceği anlamına gelir.

> [!NOTE]
> Dışarı aktarmalar ve içeri aktarmalar genellikle ortak sınıflarda veya üyelerde bildirilmelidir. Diğer bildirimler desteklenir, ancak özel, korumalı veya dahili bir üyenin dışa aktarılması veya içe aktarılması bölümün yalıtım modelini keser ve bu nedenle önerilmez.

Anlaşma türü, dışa aktarma ve içeri aktarma için tam olarak eşleşmelidir ve bir eşleşme olarak değerlendirilir. Aşağıdaki dışarı aktarmayı göz önünde bulundurun.

```vb
<Export()> 'WILL NOT match the previous import!
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export] //WILL NOT match the previous import!
public class MyLogger : IMyAddin { }
```

Bu dışarı aktarmada, `MyLogger` `IMyAddin`bunun yerine anlaşma türü olur. , Ve bu nedenle bir `IMyAddin` nesneye tür atama yapılabileceğinden, bu dışarı aktarma önceki içeri aktarma ile eşleşmez, çünkü anlaşma türleri aynı değildir. `MyLogger` `IMyAddin`

Genel olarak, Sözleşmenin adını belirtmek gerekli değildir ve çoğu sözleşme, anlaşma türü ve meta veriler bakımından tanımlanmalıdır. Ancak, belirli koşullarda, anlaşma adını doğrudan belirtmek önemlidir. En yaygın durum, bir sınıfın temel öğeler gibi ortak bir türü paylaşan birkaç değeri dışarı aktardığı durumdur. Sözleşme adı, `Import` veya `Export` özniteliğinin ilk parametresi olarak belirtilebilir. Aşağıdaki kod, bir içeri aktarma ve belirtilen sözleşme adına `MajorRevision`sahip bir dışarı aktarma gösterir.

```vb
Public Class MyExportClass

    'This one will match
    <Export("MajorRevision")>
    Public ReadOnly Property MajorRevision As Integer
        Get
            Return 4
        End Get
    End Property

    <Export("MinorRevision")>
    Public ReadOnly Property MinorRevision As Integer
        Get
            Return 16
        End Get
    End Property
End Class
```

```csharp
public class MyClass
{
    [Import("MajorRevision")]
    public int MajorRevision { get; set; }
}

public class MyExportClass
{
    [Export("MajorRevision")] //This one will match.
    public int MajorRevision = 4;

    [Export("MinorRevision")]
    public int MinorRevision = 16;
}
```

Anlaşma türü belirtilmemişse, hala içeri veya dışarı aktarma türünden çıkarsanamıyor. Ancak, anlaşma adı açıkça belirtilmiş olsa bile, aynı zamanda içeri aktarma ve dışarı aktarma için bir eşleşme olarak kabul edilmesi için anlaşma türü de tam olarak eşleşmelidir. Örneğin, `MajorRevision` alan bir dize ise, çıkarılan anlaşma türleri eşleşmez ve dışarı aktarma, aynı anlaşma adına sahip olmasına rağmen içeri aktarma ile eşleşmez.

### <a name="importing-and-exporting-a-method"></a>Bir yöntemi içeri ve dışarı aktarma

`Export` Özniteliği aynı zamanda bir yöntemi sınıf, özellik veya işlevle aynı şekilde süsde edebilir. Yöntem dışarı aktarmaları bir anlaşma türü veya sözleşme adı belirtmeli, çünkü tür çıkarsanamıyor. Belirtilen tür özel bir temsilci ya da gibi `Func`genel bir tür olabilir. Aşağıdaki sınıf adlı `DoSomething`bir yöntemi dışa aktarır.

```vb
Public Class MyAddin

    'Explicitly specifying a generic type
    <Export(GetType(Func(Of Integer, String)))>
    Public Function DoSomething(ByVal TheParam As Integer) As String
        Return Nothing 'Function body goes here
    End Function

End Class
```

```csharp
public class MyAddin
{
    //Explicitly specifying a generic type.
    [Export(typeof(Func<int, string>))]
    public string DoSomething(int TheParam);
}
```

Bu sınıfta, `DoSomething` yöntemi tek `int` bir parametre alır ve döndürür `string`. Bu dışarı aktarmayı eşleştirmek için, içeri aktarma bölümünde uygun bir üye bildirilmelidir. Aşağıdaki sınıf `DoSomething` yöntemi içeri aktarır.

```vb
Public Class MyClass1

    'Contract name must match!
    <Import()>
    Public Property MajorRevision As Func(Of Integer, String)
End Class
```

```csharp
public class MyClass
{
    [Import] //Contract name must match!
    public Func<int, string> DoSomething { get; set; }
}
```

`Func<T, T>` Nesnesinin kullanımı hakkında daha fazla bilgi için bkz <xref:System.Func%602>.

<a name="types_of_imports"></a>

## <a name="types-of-imports"></a>Içeri aktarmalar türleri

MEF, dinamik, geç, önkoşul ve isteğe bağlı olarak çeşitli içeri aktarma türlerini destekler.

### <a name="dynamic-imports"></a>Dinamik Içeri aktarmalar

Bazı durumlarda, içeri aktarma sınıfı belirli bir sözleşme adına sahip olan her türlü dışarı aktarmaları eşleştirmek isteyebilir. Bu senaryoda, sınıfı *dinamik bir içeri aktarma*bildirebilirler. Aşağıdaki içeri aktarma, sözleşme adı "TheString" olan tüm dışarı aktarma ile eşleşir.

```vb
Public Class MyClass1

    <Import("TheString")>
    Public Property MyAddin

End Class
```

```csharp
public class MyClass
{
    [Import("TheString")]
    public dynamic MyAddin { get; set; }
}
```

Anlaşma türü `dynamic` anahtar sözcükten çıkarıldığında, herhangi bir anlaşma türüyle eşleşir. Bu durumda, bir içeri aktarmanın **her zaman** eşleştirilecek bir sözleşme adı belirtmesi gerekir. (Sözleşme adı belirtilmemişse, içeri aktarma işlemi hiçbir dışarı Aktarımsız olacak şekilde değerlendirilir.) Aşağıdaki dışarı aktarımlar, önceki içeri aktarma ile eşleşir.

```vb
<Export("TheString", GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class

<Export("TheString")>
Public Class MyToolbar

End Class
```

```csharp
[Export("TheString", typeof(IMyAddin))]
public class MyLogger : IMyAddin { }

[Export("TheString")]
public class MyToolbar { }
```

Açıkça içeri aktarma sınıfı, rastgele türdeki bir nesne ile başa çıkmak için hazırlanmalıdır.

### <a name="lazy-imports"></a>Yavaş Içeri aktarmalar

Bazı durumlarda içeri aktarma sınıfı içeri aktarılan nesneye dolaylı bir başvuru gerektirebilir, böylece nesne hemen başlatılamaz. Bu senaryoda, sınıfı bir anlaşma türü `Lazy<T>`kullanarak bir *yavaş içeri aktarma* bildirebilir. Aşağıdaki içeri aktarma özelliği bir yavaş içeri aktarma bildirir.

```vb
Public Class MyClass1

    <Import()>
    Public Property MyAddin As Lazy(Of IMyAddin)

End Class
```

```csharp
public class MyClass
{
    [Import]
    public Lazy<IMyAddin> MyAddin { get; set; }
}
```

Birleşim altyapısının bakış noktasından, bir sözleşme türü `Lazy<T>` , sözleşme `T`türüyle aynı kabul edilir. Bu nedenle, önceki içeri aktarma aşağıdaki dışarı aktarma ile eşleşir.

```vb
<Export(GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export(typeof(IMyAddin))]
public class MyLogger : IMyAddin { }
```

Sözleşme adı ve sözleşme türü, daha önce "temel içeri `Import` aktarmalar ve dışarı aktarmalar" bölümünde açıklandığı gibi bir yavaş içeri aktarma özniteliğinde belirtilebilir.

### <a name="prerequisite-imports"></a>Önkoşul Içeri aktarmaları

Dışarı aktarılan MEF bölümleri genellikle doğrudan bir isteğe yanıt olarak veya eşleşen bir içeri aktarmayı doldurmanız gerektiğinde bileşim altyapısı tarafından oluşturulur. Varsayılan olarak, bir bölüm oluştururken, bileşim altyapısı parametre-daha az oluşturucuyu kullanır. Altyapının farklı bir Oluşturucu kullanmasını sağlamak için onu `ImportingConstructor` özniteliğiyle işaretleyebilirsiniz.

Her parçanın, bileşim altyapısı tarafından kullanılmak üzere yalnızca bir Oluşturucusu olabilir. Parametresiz Oluşturucu ve `ImportingConstructor` öznitelik yok ya da birden fazla `ImportingConstructor` öznitelik sağlanması bir hata üretir.

`ImportingConstructor` Özniteliği ile işaretlenmiş bir oluşturucunun parametrelerini dolduracak şekilde, bu parametrelerin hepsi otomatik olarak içeri aktarmalar olarak belirtilir. Bu, kısmi başlatma sırasında kullanılan içeri aktarmaları bildirmek için kullanışlı bir yoldur. Aşağıdaki sınıf bir içeri `ImportingConstructor` aktarma bildirmek için kullanır.

```vb
Public Class MyClass1

    Private _theAddin As IMyAddin

    'Parameterless constructor will NOT be used
    'because the ImportingConstructor
    'attribute is present.
    Public Sub New()

    End Sub

    'This constructor will be used.
    'An import with contract type IMyAddin
    'is declared automatically.
    <ImportingConstructor()>
    Public Sub New(ByVal MyAddin As IMyAddin)
        _theAddin = MyAddin
    End Sub

End Class
```

```csharp
public class MyClass
{
    private IMyAddin _theAddin;

    //Parameterless constructor will NOT be
    //used because the ImportingConstructor
    //attribute is present.
    public MyClass() { }

    //This constructor will be used.
    //An import with contract type IMyAddin is
    //declared automatically.
    [ImportingConstructor]
    public MyClass(IMyAddin MyAddin)
    {
        _theAddin = MyAddin;
    }
}
```

Varsayılan olarak, `ImportingConstructor` öznitelik, tüm parametre içeri aktarmaları için çıkarılan sözleşme türlerini ve sözleşme adlarını kullanır. Parametreleri öznitelikleri ile `Import` süsleyerek bunu geçersiz kılmak mümkündür. Bu, daha sonra sözleşme türünü ve sözleşme adını açıkça tanımlayabilirler. Aşağıdaki kod, bir üst sınıf yerine türetilmiş bir sınıfı içeri aktarmak için bu söz dizimini kullanan bir oluşturucuyu gösterir.

```vb
<ImportingConstructor()>
Public Sub New(<Import(GetType(IMySubAddin))> ByVal MyAddin As IMyAddin)

End Sub
```

```csharp
[ImportingConstructor]
public MyClass([Import(typeof(IMySubAddin))]IMyAddin MyAddin)
{
    _theAddin = MyAddin;
}
```

Özellikle, koleksiyon parametreleriyle dikkatli olmanız gerekir. Örneğin, türünde `IEnumerable<int>`bir parametre içeren `ImportingConstructor` bir Oluşturucu üzerinde belirtirseniz, içeri aktarma türü bir dışarı aktarma kümesi `int`yerine, türü `IEnumerable<int>`tek bir dışarı aktarımdan eşleşir. Türünde `int`bir dışarı aktarım kümesini eşleştirmek için parametresini `ImportMany` özniteliğiyle tasarlamanız gerekir.

`ImportingConstructor` Özniteliği tarafından içeri aktarmalar olarak belirtilen parametreler de *önkoşul içeri aktarmaları*olarak işaretlenir. MEF, normalde dışarı aktarmalar ve içeri aktarmalar oluşturmak için bir *döngüye*izin verir. Örneğin, bir döngüde nesne A 'nın, nesne a 'nın içe aktardığı, nesne a 'nın içe aktardığı yerdir. Normal koşullarda, bir döngüyle ilgili bir sorun değildir ve bileşim kapsayıcısı her iki nesneyi normal şekilde oluşturur.

Bir bölümün Oluşturucusu tarafından içeri aktarılan bir değer gerekliyse, bu nesne bir döngüye katılamaz. A nesnesi, nesne B 'nin oluşturulmadan önce oluşturulmasını gerektiriyorsa ve B nesnesi A nesnesini içeri aktardığında, bu durumda bir bileşim çözmeyecektir ve bir bileşim hatası oluşur. Bu nedenle, Oluşturucu parametrelerine göre belirtilen içeri aktarmalar, tüm ön dışarı aktarımlardan önce kullanılması gereken herhangi bir dışarı aktarımdan önce doldurulmaları gereken önkoşul içeri aktarımlardır.

### <a name="optional-imports"></a>İsteğe bağlı Içeri aktarmalar

`Import` Özniteliği, bölümün çalışması için bir gereksinim belirtir. İçeri aktarma karşılanmıyorsa, bu bölümün kompozisyonu başarısız olur ve bölüm kullanılabilir olmayacaktır.

`AllowDefault` Özelliğini kullanarak bir içeri aktarmanın *isteğe bağlı* olduğunu belirtebilirsiniz. Bu durumda, içeri aktarma işlemi kullanılabilir herhangi bir dışarı aktarımlarla eşleşmezse ve içeri aktarma özelliği özellik türü için varsayılan değer olarak ayarlanır (`null` nesne özellikleri için, `false` Boole değerleri veya sayısal için sıfır). Özellikler.) Aşağıdaki sınıf isteğe bağlı bir içeri aktarma kullanır.

```vb
Public Class MyClass1

    <Import(AllowDefault:=True)>
    Public Property thePlugin As Plugin

    'If no matching export is available,
    'thePlugin will be set to null.
End Class
```

```csharp
public class MyClass
{
    [Import(AllowDefault = true)]
    public Plugin thePlugin { get; set; }

    //If no matching export is available,
    //thePlugin will be set to null.
}
```

### <a name="importing-multiple-objects"></a>Birden çok nesne içeri aktarılıyor

`Import` Özniteliği yalnızca bir ve yalnızca bir dışarı aktarma ile eşleştiğinde başarılı bir şekilde oluşturulur. Diğer durumlar, bir bileşim hatası oluşturur. Aynı sözleşmeyle eşleşen birden fazla dışarı aktarmayı içeri aktarmak için `ImportMany` özniteliğini kullanın. Bu öznitelikle işaretlenen içeri aktarmalar her zaman isteğe bağlıdır. Örneğin, hiçbir eşleşen dışarı aktarma yoksa, bileşim başarısız olmaz. Aşağıdaki sınıf, türünde `IMyAddin`herhangi bir sayıda dışarı aktarma içeri aktarır.

```vb
Public Class MyClass1

    <ImportMany()>
    Public Property MyAddin As IEnumerable(Of IMyAddin)

End Class
```

```csharp
public class MyClass
{
    [ImportMany]
    public IEnumerable<IMyAddin> MyAddin { get; set; }
}
```

İçeri aktarılan diziye, normal `IEnumerable<T>` sözdizimi ve yöntemleri kullanılarak erişilebilir. Bunun yerine sıradan bir Array (`IMyAddin[]`) kullanmak da mümkündür.

Bu model, `Lazy<T>` söz dizimi ile birlikte kullandığınızda çok önemli olabilir. Örneğin,, ve `ImportMany` `IEnumerable<T>` `Lazy<T>`kullanarak, dolaylı başvuruları herhangi bir sayıda nesneye aktarabilir ve yalnızca gerekli olanları örnekleyebilirsiniz. Aşağıdaki sınıf bu kalıbı gösterir.

```vb
Public Class MyClass1

    <ImportMany()>
    Public Property MyAddin As IEnumerable(Of Lazy(Of IMyAddin))

End Class
```

```csharp
public class MyClass
{
    [ImportMany]
    public IEnumerable<Lazy<IMyAddin>> MyAddin { get; set; }
}
```

<a name="avoiding_discovery"></a>

## <a name="avoiding-discovery"></a>Bulmaktan kaçınma

Bazı durumlarda, bir bölümün bir kataloğun parçası olarak bulunmasını engellemek isteyebilirsiniz. Örneğin, bölüm, öğesinden Devralınana yönelik bir temel sınıf olabilir, ancak kullanılmaz. Bunu yapmanın iki yolu vardır. İlk olarak, bölüm sınıfında `abstract` anahtar sözcüğünü kullanabilirsiniz. Soyut sınıflar hiçbir şekilde dışa aktarma sağlamaz, ancak onlardan türetilen sınıflara devralınan dışarı aktarmalar sağlayabilir.

Sınıf soyut hale getiril, `PartNotDiscoverable` özniteliği ile süslenebilir. Bu öznitelikle donatılmış bir bölüm, hiçbir katalogda yer almaz. Aşağıdaki örnekte bu desenler gösterilmektedir. `DataOne`, katalog tarafından keşfedilir. `DataTwo` Soyut olduğundan, bulunamayacaktır. Özniteliği kullanılmasından bu yana `DataThree` bulunamayacaktır. `PartNotDiscoverable`

```vb
<Export()>
Public Class DataOne
    'This part will be discovered
    'as normal by the catalog.
End Class

<Export()>
Public MustInherit Class DataTwo
    'This part will not be discovered
    'by the catalog.
End Class

<PartNotDiscoverable()>
<Export()>
Public Class DataThree
    'This part will also not be discovered
    'by the catalog.
End Class
```

```csharp
[Export]
public class DataOne
{
    //This part will be discovered
    //as normal by the catalog.
}

[Export]
public abstract class DataTwo
{
    //This part will not be discovered
    //by the catalog.
}

[PartNotDiscoverable]
[Export]
public class DataThree
{
    //This part will also not be discovered
    //by the catalog.
}
```

<a name="metadata_and_metadata_views"></a>

## <a name="metadata-and-metadata-views"></a>Meta veriler ve meta veri görünümleri

Dışarı aktarmalar, kendileri hakkında, *meta veri*olarak bilinen ek bilgiler sağlayabilir. Meta veriler, aktarılan nesnenin özelliklerini içeri aktarma bölümüne iletmek için kullanılabilir. İçeri aktarma bölümü bu verileri kullanarak hangi dışarı aktarımların kullanılacağını seçebilir veya onu oluşturmak zorunda kalmadan bir dışarı aktarma hakkında bilgi toplayabilir. Bu nedenle, meta verilerin kullanılması için bir içeri aktarmanın yavaş olması gerekir.

Meta verileri kullanmak için genellikle meta veri *görünümü*olarak bilinen bir arabirim bildirirsiniz, bu da hangi meta verilerin kullanılabilir olacağını bildirir. Meta veri görünümü arabiriminin yalnızca özellikleri olmalıdır ve bu özelliklerin `get` erişimcileri olmalıdır. Aşağıdaki arabirim bir örnek meta veri görünümüdür.

```vb
Public Interface IPluginMetadata

    ReadOnly Property Name As String

    <DefaultValue(1)>
    ReadOnly Property Version As Integer

End Interface
```

```csharp
public interface IPluginMetadata
{
    string Name { get; }

    [DefaultValue(1)]
    int Version { get; }
}
```

Ayrıca, meta veri görünümü olarak genel bir koleksiyon `IDictionary<string, object>`kullanmak da mümkündür, ancak bu, tür denetimi avantajlarından yararlanır ve kaçınılması gerekir.

Normalde, meta veri görünümündeki adlı tüm özellikler zorunludur ve bunları sağlamayan tüm dışarı aktarımlar bir eşleşme olarak değerlendirilmez. `DefaultValue` Özniteliği bir özelliğin isteğe bağlı olduğunu belirtir. Özellik dahil değilse, parametresi `DefaultValue`olarak belirtilen varsayılan değere atanır. Aşağıdakiler meta verilerle donatılmış iki farklı sınıftır. Bu sınıfların her ikisi de önceki meta veri görünümüyle eşleşir.

```vb
<Export(GetType(IPlugin))>
<ExportMetadata("Name", "Logger")>
<ExportMetadata("Version", 4)>
Public Class MyLogger
    Implements IPlugin

End Class

'Version is not required because of the DefaultValue
<Export(GetType(IPlugin))>
<ExportMetadata("Name", "Disk Writer")>
Public Class DWriter
    Implements IPlugin

End Class
```

```csharp
[Export(typeof(IPlugin)),
    ExportMetadata("Name", "Logger"),
    ExportMetadata("Version", 4)]
public class Logger : IPlugin
{
}

[Export(typeof(IPlugin)),
    ExportMetadata("Name", "Disk Writer")]
    //Version is not required because of the DefaultValue
public class DWriter : IPlugin
{
}
```

Meta veriler özniteliği `Export` `ExportMetadata` kullanılarak öznitelikten sonra ifade edilir. Her meta veri parçası bir ad/değer çiftinden oluşur. Meta verilerin ad kısmı meta veri görünümündeki uygun özelliğin adıyla eşleşmelidir ve değer bu özelliğe atanır.

Varsa, hangi meta veri görünümünün kullanımda olacağını belirten içeri aktarıcıdır. Meta veri içeren bir içeri aktarma, için `Lazy<T,T>`ikinci tür parametresi olarak meta veri arabirimi ile bir yavaş içeri aktarma olarak belirtilir. Aşağıdaki sınıf önceki bölümü meta verilerle içe aktarır.

```vb
Public Class Addin

    <Import()>
    Public Property plugin As Lazy(Of IPlugin, IPluginMetadata)
End Class
```

```csharp
public class Addin
{
    [Import]
    public Lazy<IPlugin, IPluginMetadata> plugin;
}
```

Birçok durumda, kullanılabilir içeri aktarmalar aracılığıyla ayrıştırılacak ve yalnızca bir `ImportMany` tane seçip örnekleyerek veya bir koleksiyonu belirli bir koşulla eşleşecek şekilde filtreleyecek şekilde meta verileri özniteliğiyle birleştirmek isteyeceksiniz. Aşağıdaki sınıf yalnızca `IPlugin` "günlükçü" `Name` değerine sahip nesneleri örnekleyen.

```vb
Public Class User

    <ImportMany()>
    Public Property plugins As IEnumerable(Of Lazy(Of IPlugin, IPluginMetadata))

    Public Function InstantiateLogger() As IPlugin

        Dim logger As IPlugin
        logger = Nothing

        For Each Plugin As Lazy(Of IPlugin, IPluginMetadata) In plugins
            If Plugin.Metadata.Name = "Logger" Then
                logger = Plugin.Value
            End If
        Next
        Return logger
    End Function

End Class
```

```csharp
public class User
{
    [ImportMany]
    public IEnumerable<Lazy<IPlugin, IPluginMetadata>> plugins;

    public IPlugin InstantiateLogger()
    {
        IPlugin logger = null;

        foreach (Lazy<IPlugin, IPluginMetadata> plugin in plugins)
        {
            if (plugin.Metadata.Name == "Logger")
                logger = plugin.Value;
        }
        return logger;
    }
}
```

<a name="import_and_export_inheritance"></a>

## <a name="import-and-export-inheritance"></a>Devralmayı içeri ve dışarı aktarma

Bir sınıf bir bölümden devralırsa, bu sınıf da bir parça olabilir. İçeri aktarmalar her zaman alt sınıflar tarafından devralınır. Bu nedenle, bir parçanın bir alt sınıfı her zaman üst sınıfı ile aynı içeri aktarmaları olan bir bölüm olacaktır.

Özniteliği kullanılarak belirtilen dışarı aktarmalar `Export` , alt sınıflar tarafından devralınmaz. Ancak, bir bölüm `InheritedExport` özniteliğini kullanarak kendisini dışarı aktarabilir. Bölümün alt sınıfları, sözleşme adı ve anlaşma türü dahil olmak üzere aynı dışarı aktarmayı alır ve verir. Bir `Export` özniteliğin aksine, `InheritedExport` üye düzeyinde değil yalnızca sınıf düzeyinde uygulanabilir. Bu nedenle, üye düzeyinde dışarı aktarımlar hiçbir şekilde devralınmaz.

Aşağıdaki dört sınıf içeri ve dışarı aktarma devralma ilkelerini gösterir. `NumTwo`öğesinden `NumOne` devraldığından`IMyData`içeri aktarma işlemi yapılır.`NumTwo` Sıradan dışarı aktarmalar devralınmaz, bu `NumTwo` nedenle hiçbir şeyi dışarı aktarmaz. `NumFour`öğesinden `NumThree`devralır. Kullanıldığı için, Sözleşme`NumFour` türünde`NumThree`bir dışarı aktarma işlemi vardır. `InheritedExport` `NumThree` Üye düzeyinde dışarı aktarımlar hiçbir şekilde devralınmaz, `IMyData` bu nedenle dışarı aktarılmaz.

```vb
<Export()>
Public Class NumOne
    <Import()>
    Public Property MyData As IMyData
End Class

Public Class NumTwo
    Inherits NumOne

    'Imports are always inherited, so NumTwo will
    'Import IMyData

    'Ordinary exports are not inherited, so
    'NumTwo will NOT export anything.  As a result it
    'will not be discovered by the catalog!

End Class

<InheritedExport()>
Public Class NumThree

    <Export()>
    Public Property MyData As IMyData

    'This part provides two exports, one of
    'contract type NumThree, and one of
    'contract type IMyData.

End Class

Public Class NumFour
    Inherits NumThree

    'Because NumThree used InheritedExport,
    'this part has one export with contract
    'type NumThree.

    'Member-level exports are never inherited,
    'so IMyData is not exported.

End Class
```

```csharp
[Export]
public class NumOne
{
    [Import]
    public IMyData MyData { get; set; }
}

public class NumTwo : NumOne
{
    //Imports are always inherited, so NumTwo will
    //import IMyData.

    //Ordinary exports are not inherited, so
    //NumTwo will NOT export anything. As a result it
    //will not be discovered by the catalog!
}

[InheritedExport]
public class NumThree
{
    [Export]
    Public IMyData MyData { get; set; }

    //This part provides two exports, one of
    //contract type NumThree, and one of
    //contract type IMyData.
}

public class NumFour : NumThree
{
    //Because NumThree used InheritedExport,
    //this part has one export with contract
    //type NumThree.

    //Member-level exports are never inherited,
    //so IMyData is not exported.
}
```

Bir `InheritedExport` öznitelikle ilişkili meta veriler varsa, bu meta veriler de devralınacaktır. (Daha fazla bilgi için önceki "meta veriler ve meta veri görünümleri" bölümüne bakın.) Devralınan meta veriler alt sınıf tarafından değiştirilemez. Ancak, aynı sözleşme adı ve anlaşma `InheritedExport` türüyle özniteliği yeniden bildirerek, ancak yeni meta veriler ile, alt sınıf devralınan meta verileri yeni meta verilerle değiştirebilir. Aşağıdaki sınıf bu ilkeyi gösterir. Bölüm öğesinden `Logger` devralır ve `InheritedExport` özniteliği içerir. `MegaLogger` Durum `MegaLogger` adlı yeni meta verileri yeniden bildirdiğinden, ' den `Logger`adı ve sürüm meta verilerini içermez.

```vb
<InheritedExport(GetType(IPlugin))>
<ExportMetadata("Name", "Logger")>
<ExportMetadata("Version", 4)>
Public Class Logger
    Implements IPlugin

    'Exports with contract type IPlugin
    'and metadata "Name" and "Version".
End Class

Public Class SuperLogger
    Inherits Logger

    'Exports with contract type IPlugin and
    'metadata "Name" and "Version", exactly the same
    'as the Logger class.

End Class

<InheritedExport(GetType(IPlugin))>
<ExportMetadata("Status", "Green")>
Public Class MegaLogger
    Inherits Logger

    'Exports with contract type IPlugin and
    'metadata "Status" only. Re-declaring
    'the attribute replaces all metadata.

End Class
```

```csharp
[InheritedExport(typeof(IPlugin)),
    ExportMetadata("Name", "Logger"),
    ExportMetadata("Version", 4)]
public class Logger : IPlugin
{
    //Exports with contract type IPlugin and
    //metadata "Name" and "Version".
}

public class SuperLogger : Logger
{
    //Exports with contract type IPlugin and
    //metadata "Name" and "Version", exactly the same
    //as the Logger class.
}

[InheritedExport(typeof(IPlugin)),
    ExportMetadata("Status", "Green")]
public class MegaLogger : Logger        {
    //Exports with contract type IPlugin and
    //metadata "Status" only. Re-declaring
    //the attribute replaces all metadata.
}
```

Meta verileri geçersiz kılmak için `InheritedExport` özniteliği yeniden bildirirken, anlaşma türlerinin aynı olduğundan emin olun. (Önceki örnekte, `IPlugin` Sözleşme türüdür.) Farklıysa, ikinci öznitelik bölümden ikinci bir bağımsız dışarı aktarma işlemi oluşturacaktır. Genellikle bu, önceki örnekte gösterildiği gibi bir `InheritedExport` özniteliği geçersiz kıldığınızda anlaşma türünü açıkça belirtmeniz gerektiği anlamına gelir.

Arabirimler doğrudan oluşturulamadıklarından, genellikle veya `Export` `Import` öznitelikleriyle birlikte tasarlanamazlar. Bununla birlikte, bir arabirim, arabirim düzeyinde bir `InheritedExport` öznitelikle ilişkilendirilebilir ve ilgili tüm meta verilerle birlikte dışarı aktarma işlemi herhangi bir uygulama sınıfı tarafından devralınır. Ancak, arabirim bir bölüm olarak kullanılamaz.

<a name="custom_export_attributes"></a>

## <a name="custom-export-attributes"></a>Özel dışarı aktarma öznitelikleri

Temel dışa aktarma öznitelikleri `Export` ve `InheritedExport`, meta verileri öznitelik özellikleri olarak içerecek şekilde genişletilebilir. Bu teknik, benzer meta verileri birçok parçaya uygulamak veya meta veri özniteliklerinin devralma ağacını oluşturmak için faydalıdır.

Özel bir öznitelik, anlaşma türünü, anlaşma adını veya diğer meta verileri belirtebilir. Özel bir öznitelik tanımlamak için, (veya `ExportAttribute` `InheritedExportAttribute`) öğesinden devralan bir sınıf, `MetadataAttribute` özniteliğiyle birlikte tasarlanmalıdır. Aşağıdaki sınıf özel bir özniteliği tanımlar.

```vb
<MetadataAttribute()>
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=false)>
Public Class MyAttribute
    Inherits ExportAttribute

    Public Property MyMetadata As String

    Public Sub New(ByVal myMetadata As String)
        MyBase.New(GetType(IMyAddin))

        myMetadata = myMetadata
    End Sub

End Class
```

```csharp
[MetadataAttribute]
[AttributeUsage(AttributeTargets.Class, AllowMultiple=false)]
public class MyAttribute : ExportAttribute
{
    public MyAttribute(string myMetadata)
        : base(typeof(IMyAddin))
    {
        MyMetadata = myMetadata;
    }

    public string MyMetadata { get; private set; }
}
```

Bu sınıf, anlaşma türü `MyAttribute` `IMyData` ile adlı özel bir özniteliği ve adında `MyMetadata`bazı meta verileri tanımlar. `MetadataAttribute` Özniteliği ile işaretlenmiş bir sınıftaki tüm özellikler özel özniteliğinde tanımlanmış meta veriler olarak kabul edilir. Aşağıdaki iki bildirim eşdeğerdir.

```vb
<Export(GetType(IMyAddin))>
<ExportMetadata("MyMetadata", "theData")>
Public Property myAddin As MyAddin
```

```vb
<MyAttribute("theData")>
Public Property myAddin As MyAddin
```

```csharp
[Export(typeof(IMyAddin)),
    ExportMetadata("MyMetadata", "theData")]
public MyAddin myAddin { get; set; }
```

```csharp
[MyAttribute("theData")]
public MyAddin myAddin { get; set; }
```

İlk bildirimde, anlaşma türü ve meta veriler açıkça tanımlanmıştır. İkinci bildirimde, anlaşma türü ve meta veriler, özelleştirilmiş öznitelikte örtülü olarak bulunur. Özellikle, büyük miktarda özdeş meta verilerin birçok parçaya uygulanması gerektiği durumlarda (örneğin, yazar veya telif hakkı bilgileri), özel bir öznitelik kullanmak çok fazla zaman ve çoğaltma kazandırabilir. Ayrıca, çeşitlere izin vermek için özel özniteliklerin devralma ağaçları oluşturulabilir.

Özel bir öznitelikte isteğe bağlı meta veri oluşturmak için `DefaultValue` özniteliğini kullanabilirsiniz. Bu öznitelik özel öznitelik sınıfındaki bir özelliğe uygulandığında, düzenlenmiş özelliğin isteğe bağlı olduğunu ve bir dışarı aktarma tarafından sağlanması gerektiğini belirtir. Özelliği için bir değer sağlanmadığında, özellik türü (genellikle `null`, `false`, veya 0) için varsayılan değer atanır.

<a name="creation_policies"></a>

## <a name="creation-policies"></a>Oluşturma Ilkeleri

Bir parça bir içeri aktarma belirttiğinde ve bileşim gerçekleştirildiğinde, bileşim kapsayıcısı eşleşen bir dışarı aktarma bulmaya çalışır. İçeri aktarma işlemi başarıyla dışarı aktarma ile eşleşiyorsa, içeri aktarma üyesi dışa aktarılan nesnenin bir örneğine ayarlanır. Bu örneğin nereden geldiği, dışa aktarılan bölümün *oluşturma ilkesi*tarafından denetlenir.

Olası iki oluşturma ilkesi *paylaşılır* ve *paylaşılmaz*. Paylaşılan bir oluşturma ilkesinin bulunduğu bir bölüm, söz konusu sözleşmenin bir parçası için kapsayıcıdaki her içeri aktarma arasında paylaşılır. Bileşim altyapısı bir eşleşme bulduğunda ve bir içeri aktarma özelliği ayarlamaya sahipse, yalnızca bir tane yoksa, bölümün yeni bir kopyasını oluşturur. Aksi takdirde, mevcut kopyayı sağlar. Bu, birçok nesnenin aynı bölüme başvurmuş olabileceği anlamına gelir. Bu tür parçalar birçok yerden değiştirilebilen iç duruma dayanmamalıdır. Bu ilke statik bölümler, hizmet sağlayan parçalar ve çok fazla bellek veya diğer kaynakları kullanan parçalar için uygundur.

Dışarı aktarmalarından biri için eşleşen bir içeri aktarma bulunduğunda, paylaşılmayan oluşturma ilkesini içeren bir bölüm oluşturulur. Bu nedenle, kapsayıcının dışarı aktarılan sözleşmelerinden biriyle eşleşen kapsayıcıdaki her içeri aktarma işlemi için yeni bir kopya oluşturulacak. Bu kopyaların iç durumu paylaşılmayacak. Bu ilke, her içeri aktarmanın kendi iç durumunu gerektirdiği parçalar için uygundur.

İçeri aktarma ve dışarı aktarma, bir bölümün oluşturma ilkesini, veya `Shared` `Any`değerlerinin `NonShared`arasından belirtebilir. Varsayılan değer `Any` içeri ve dışarı aktarma içindir. Yalnızca `Shared` aynısınıbelirten`NonShared` veya belirten bir içeri aktarma ile eşleşen bir dışarı aktarma işlemi. `Any` Benzer şekilde, `Shared` veya `NonShared` belirten bir içeri aktarma yalnızca aynısını belirten veya belirten `Any`bir dışarı aktarma ile eşleşir. Uyumsuz oluşturma ilkelerine sahip içeri aktarmalar ve dışarı aktarmalar, sözleşme adı veya sözleşme türü eşleşme olmayan bir içeri ve dışarı aktarma ile aynı şekilde bir eşleşme olarak kabul edilmez. Hem içeri ve dışarı aktarma `Any`hem de bir oluşturma ilkesi ve için `Any`varsayılan değer belirtmez, oluşturma ilkesi varsayılan olarak paylaşılacaktır.

Aşağıdaki örnek, oluşturma ilkelerini belirten içeri ve dışarı aktarmaları gösterir. `PartOne`bir oluşturma ilkesi belirtmez, bu nedenle varsayılan olur `Any`. `PartTwo`bir oluşturma ilkesi belirtmez, bu nedenle varsayılan olur `Any`. Hem içeri hem de dışarı aktarma varsayılan `Any` `PartOne` olarak paylaşılacak. `PartThree`bir `Shared` oluşturma ilkesi belirtir, `PartThree` bu `PartTwo` nedenle aynı kopyasını `PartOne`paylaşır. `PartFour`bir `NonShared` oluşturma ilkesi belirtir, bu `PartFour` nedenle içinde `PartFive`paylaşılmayacak. `PartSix`bir `NonShared` oluşturma ilkesi belirtir. `PartFive`ve `PartSix` her biri ayrı `PartFour`birer kopyasını alır. `PartSeven`bir `Shared` oluşturma ilkesi belirtir. Oluşturma `PartFour` ilkesiyledışarı`PartSeven` aktarılmış olmadığından ,içeriaktarmahiçbirşeyleeşleşmezvedoldurulmayacaktır.`Shared`

```vb
<Export()>
Public Class PartOne
    'The default creation policy for an export is Any.
End Class

Public Class PartTwo

    <Import()>
    Public Property partOne As PartOne

    'The default creation policy for an import is Any.
    'If both policies are Any, the part will be shared.

End Class

Public Class PartThree

    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>
    Public Property partOne As PartOne

    'The Shared creation policy is explicitly specified.
    'PartTwo and PartThree will receive references to the
    'SAME copy of PartOne.

End Class

<Export()>
<PartCreationPolicy(CreationPolicy.NonShared)>
Public Class PartFour
    'The NonShared creation policy is explicitly specified.
End Class

Public Class PartFive

    <Import()>
    Public Property partFour As PartFour

    'The default creation policy for an import is Any.
    'Since the export's creation policy was explicitly
    'defined, the creation policy for this property will
    'be non-shared.

End Class

Public Class PartSix

    <Import(RequiredCreationPolicy:=CreationPolicy.NonShared)>
    Public Property partFour As PartFour

    'Both import and export specify matching creation
    'policies.  PartFive and PartSix will each receive
    'SEPARATE copies of PartFour, each with its own
    'internal state.

End Class

Public Class PartSeven

    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>
    Public Property partFour As PartFour

    'A creation policy mismatch.  Because there is no
    'exported PartFour with a creation policy of Shared,
    'this import does not match anything and will not be
    'filled.

End Class
```

```csharp
[Export]
public class PartOne
{
    //The default creation policy for an export is Any.
}

public class PartTwo
{
    [Import]
    public PartOne partOne { get; set; }

    //The default creation policy for an import is Any.
    //If both policies are Any, the part will be shared.
}

public class PartThree
{
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]
    public PartOne partOne { get; set; }

    //The Shared creation policy is explicitly specified.
    //PartTwo and PartThree will receive references to the
    //SAME copy of PartOne.
}

[Export]
[PartCreationPolicy(CreationPolicy.NonShared)]
public class PartFour
{
    //The NonShared creation policy is explicitly specified.
}

public class PartFive
{
    [Import]
    public PartFour partFour { get; set; }

    //The default creation policy for an import is Any.
    //Since the export's creation policy was explicitly
    //defined, the creation policy for this property will
    //be non-shared.
}

public class PartSix
{
    [Import(RequiredCreationPolicy = CreationPolicy.NonShared)]
    public PartFour partFour { get; set; }

    //Both import and export specify matching creation
    //policies.  PartFive and PartSix will each receive
    //SEPARATE copies of PartFour, each with its own
    //internal state.
}

public class PartSeven
{
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]
    public PartFour partFour { get; set; }

    //A creation policy mismatch.  Because there is no
    //exported PartFour with a creation policy of Shared,
    //this import does not match anything and will not be
    //filled.
}
```

<a name="life_cycle_and_disposing"></a>

## <a name="life-cycle-and-disposing"></a>Yaşam döngüsü ve elden atma

Parçalar bileşim kapsayıcısında barındırıldığından, bunların yaşam döngüsü sıradan nesnelerden daha karmaşık olabilir. Parçalar, iki önemli yaşam döngüyle ilgili arabirimler uygulayabilir: `IDisposable` ve `IPartImportsSatisfiedNotification`.

Çalışma veya kaynakların serbest bırakılması gereken, .NET Framework nesneler için her zamanki gibi, çalışması gereken bölümlerin uygulanması `IDisposable`gerekir. Ancak, kapsayıcı parçalar için başvuruları oluşturduğundan ve sakladığı için, yalnızca bir bölüme sahip olan kapsayıcı üzerinde `Dispose` yöntemi çağırmalıdır. Kapsayıcının kendisi `IDisposable`ve içindeki `Dispose` Temizleme işleminin bir kısmı, sahip olduğu tüm bölümleri çağırır `Dispose` . Bu nedenle, derleme kapsayıcısını her zaman ve sahip olduğu tüm parçalar artık gerekli olmadığında atmalısınız.

Uzun süreli oluşturma kapsayıcıları için, paylaşılmayan bir oluşturma ilkesiyle bölümlere göre bellek tüketimi bir sorun olabilir. Bu paylaşılmayan bölümler birden çok kez oluşturulabilir ve kapsayıcının kendisi atılana kadar atılamaz. Bu sorunu ele almak için kapsayıcı `ReleaseExport` yöntemini sağlar. Bu yöntemi paylaşılmayan bir dışarı aktarma üzerinde çağırmak, bu dışarı aktarmayı bileşim kapsayıcısından kaldırır ve bunu ortadan kaldırır. Yalnızca kaldırılan dışarı aktarma tarafından kullanılan ve bu nedenle ağacın üzerinde kullanılan parçalar da kaldırılır ve silinir. Bu şekilde, kaynaklar bileşim kapsayıcısının kendisini elden çıkarmadan geri kazanılabilirler.

`IPartImportsSatisfiedNotification`adlı `OnImportsSatisfied`bir yöntemi içerir. Bu yöntem, oluşturma işlemi tamamlandığında ve bölümün içeri aktarmaları kullanıma hazırlandığında arabirimini uygulayan herhangi bir bölümde bileşim kapsayıcısı tarafından çağırılır. Bölümler, diğer parçaların içeri aktarmalarını dolduracak şekilde bileşim altyapısı tarafından oluşturulur. Bir bölümün içeri aktarmaları bir şekilde ayarlanmadan önce, bu değerler `ImportingConstructor` öznitelik kullanılarak önkoşul olarak belirtilmediği sürece, Bölüm oluşturucusunda içeri aktarılan değerleri kullanan veya bunları değiştiren herhangi bir başlatma gerçekleştiremezsiniz. Bu normal olarak tercih edilen yöntemdir, ancak bazı durumlarda, Oluşturucu Ekleme kullanılamıyor olabilir. Bu durumlarda, ' de `OnImportsSatisfied`başlatma gerçekleştirilebilir ve bölümünün uygulanması `IPartImportsSatisfiedNotification`gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Channel 9 videosu: Uygulamalarınızı Managed Extensibility Framework açın](https://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)
- [Channel 9 videosu: Managed Extensibility Framework (MEF) 2,0](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)
