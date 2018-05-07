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
ms.openlocfilehash: baa66f11404e2cee83b4d4b32ba02544c9438d7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="attributed-programming-model-overview-mef"></a>Öznitelikli Programlama Modeline Genel Bakış (MEF)
İçinde Yönetilen Genişletilebilirlik Çerçevesi (MEF), bir *programlama modeli* MEF faaliyet kavramsal nesneler kümesini tanımlayan belirli bir yöntemdir. Bu kavramsal nesneler bölümleri, içeri aktarmalar ve dışarı aktarma içerir. MEF bu nesneleri kullanır, ancak nasıl temsil belirtmiyor. Bu nedenle, çok çeşitli programlama modelleri programlama modelleri de dahil olmak üzere özelleştirilebilir mümkün.  
  
 Programlama modeli MEF kullanılan varsayılan *öznitelikli programlama modeli*. Öznitelikli Programlama modeli bölümleri, içeri aktarmalar, dışa aktarır ve diğer nesneleri sıradan .NET Framework sınıflarını tasarlayan öznitelikler ile tanımlanır. Bu konu öznitelikli programlama modeli tarafından sağlanan özniteliklerin bir MEF uygulaması oluşturmak için nasıl kullanılacağını açıklar.  
  
<a name="import_and_export_basics"></a>   
## <a name="import-and-export-basics"></a>İçeri ve dışarı aktarma temelleri  
 Bir *verme* kapsayıcı diğer bölümlerinde bir bölümü sağlayan bir değerdir ve bir *alma* erişilebilir dışarı doldurulması için bu kapsayıcıya aktarımlardan açıklayan bir bölüm bir gereksinimdir. Öznitelikli Programlama modeli içeri ve dışarı aktarmalar sınıflar ve üyeleri ile tasarlayarak bildirilir `Import` ve `Export` öznitelikleri. `Export` Özniteliği işaretleme sınıf, alan, özellik veya yöntem sırada `Import` özniteliği bir alan, özelliği veya oluşturucusu parametre tasarlamanız.  
  
 Bir verme ile eşleştirilmesini alma, içeri ve dışarı aktarma aynı olması gerekir *sözleşme*. Anlaşma adı verilen bir dize türünden oluşur *sözleşme adı*, çağrılan dışarı aktarılan ya da içeri aktarılan nesne türünü *sözleşme türü*. Yalnızca sözleşme adı ve sözleşme türü eşleşmesi verme belirli bir alma işlemi gerçekleştirmek için değerlendirilir.  
  
 Ya da sözleşme parametrelerinin her ikisi de kapalı veya açık olabilir. Aşağıdaki kod temel alma bildiren bir sınıfı gösterir.  
  
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
  
 Bu içeri `Import` öznitelik türünün bir sözleşme veya iliştirilmiş bir sözleşme adı parametresi vardır. Bu nedenle, her ikisi de tasarlanmış özellikten. Bu durumda, anlaşma türü olacak `IMyAddin`, ve sözleşme adı anlaşma türünden oluşturulan benzersiz bir dize olacaktır. (Diğer bir deyişle, sözleşme adı yalnızca, adları türünden de çıkartılan dışarı aktarma ile eşleşir `IMyAddin`.)  
  
 Önceki içeri eşleşen bir dışarı aktarma gösterir.  
  
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
  
 Bu dışarı aktarma sözleşme türüdür `IMyAddin` bir parametresi olarak belirtildiğinden `Export` özniteliği. Dışarı aktarılan tür ya da aynı sözleşme türü olması gerekir, sözleşme türden türetilmiş veya arabirim ise sözleşme türü uygulamak. Bu dışarı aktarma, gerçek tür içinde `MyLogger` arabirimini uygulayan `IMyAddin`. Sözleşme adı bu dışarı aktarma önceki içeri eşleşir anlamına gelir anlaşma türü ile sonuçlandı.  
  
> [!NOTE]
>  Dışarı ve içeri aktarmalar, ortak sınıf veya üye üzerinde bildirilmelidir. Diğer bildirimler desteklenir, ancak veya özel verme, korumalı veya dahili bir üyeyi bölümü için yalıtım modelini keser ve bu nedenle önerilmez.  
  
 Sözleşme türü dışarı ve içeri aktarma bir eşleşme olarak kabul edilmesi için için tam olarak eşleşmelidir. Aşağıdaki dışarı göz önünde bulundurun.  
  
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
  
 Bu dışarı aktarma sözleşme türüdür `MyLogger` yerine `IMyAddin`. Olsa bile `MyLogger` uygulayan `IMyAddin`ve bu nedenle dönüştürülebilir bir `IMyAddin` nesnesi, bu dışarı aktarma sözleşme türleri aynı olmadığından önceki içeri eşleşmez.  
  
 Genel olarak, sözleşme adı belirtmek gerekli değildir ve çoğu sözleşmeleri sözleşme türü ve meta veri bakımından tanımlanması gerekir. Ancak, belirli koşullar altında doğrudan sözleşme adı belirtmek önemlidir. Bir sınıf temelleri gibi ortak bir türü paylaşan değerlerden verdiğinde en yaygın bir durumdur. Sözleşme adı ilk parametresi belirtilebilir `Import` veya `Export` özniteliği. Aşağıdaki kod bir alma ve verme belirtilen sözleşme adıyla gösterir `MajorRevision`.  
  
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
  
 Anlaşma türü belirtilmezse, bunu hala içe veya dışa aktarma türünden çıkarılabilir olacaktır. Ancak, sözleşme adı açıkça belirtilmiş olsa bile, anlaşma türü de tam olarak alma ve verme bir eşleşme olarak kabul edilmesi için eşleşmelidir. Örneğin, varsa `MajorRevision` alanı bir dize olsaydı, çıkarılan anlaşma türleri eşleşmiyor ve dışarı aktarma, aynı sözleşme adına sahip olmasına rağmen alma, aynı olmamalıdır.  
  
### <a name="importing-and-exporting-a-method"></a>İçeri ve dışarı aktarma yöntemi  
 `Export` Özniteliği de tasarlamanız bir yöntem aynı şekilde bir sınıf, özellik veya işlev. Türü çıkarsanamıyor gibi yöntemi dışarı sözleşme türü veya sözleşme adı belirtmeniz gerekir. Belirtilen tür gibi özel bir temsilci ya da genel bir tür olabilir `Func`. Aşağıdaki sınıf adlı bir yöntem verir `DoSomething`.  
  
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
    [Export(typeof(Func<int, string>)]  
    public string DoSomething(int TheParam);  
}  
```  
  
 Bu sınıftaki `DoSomething` yöntemi alır tek bir `int` parametre ve döndürür bir `string`. Bu dışarı aktarma eşleştirmek için içeri aktarılan bölüm uygun bir üye bildirmeniz gerekir. Aşağıdaki sınıf içeri aktarmalar `DoSomething` yöntemi.  
  
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
  
 Kullanımı hakkında daha fazla bilgi için `Func<T, T>` nesne için bkz: <xref:System.Func%602>.  
  
<a name="types_of_imports"></a>   
## <a name="types-of-imports"></a>İçeri aktarmalar türleri  
 Yavaş, önkoşul ve isteğe bağlı dinamik dahil olmak üzere birkaç alma MEF destek türleri.  
  
### <a name="dynamic-imports"></a>Dinamik içeri aktarmalar  
 Bazı durumlarda, içeri aktarma sınıfı belirli sözleşme adına sahip dışarı herhangi bir türde eşleşen isteyebilirsiniz. Bu senaryoda sınıf bildirebilir bir *dinamik alma*. Aşağıdaki içeri aktarma tüm verme sözleşme adı "Width" ile eşleşir.  
  
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
  
 Ne zaman anlaşma türü sözcüğünden çıkarıldığında `dynamic` anahtar sözcüğü, herhangi bir sözleşme türü ile eşleşir. Bu durumda, bir içeri aktarma gereken **her zaman** eşleştirilecek bir sözleşme adı belirtin. (Hiçbir sözleşme adı belirtilirse, alma işlemi hiçbir dışarı aktarma eşleşecek şekilde kabul edilir.) Aşağıdaki dışarı her ikisi de önceki içeri eşleşir.  
  
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
  
 Belli ki, içeri aktarma sınıfı rasgele türünde bir nesne mücadele etmek için hazırlanması gerekir.  
  
### <a name="lazy-imports"></a>Yavaş içeri aktarmalar  
 Böylece nesne hemen oluşturulmadı bazı durumlarda, içeri aktarılan nesne için dolaylı bir başvuru alma sınıfı gerektirebilir. Bu senaryoda sınıf bildirebilir bir *yavaş alma* anlaşma türünü kullanarak `Lazy<T>`. Aşağıdaki içeri aktarma özelliği bir yavaş alma bildirir.  
  
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
  
 Bir sözleşme açısından bakıldığında bileşim motoru, türü `Lazy<T>` anlaşma türü ile aynı olarak kabul edilir `T`. Bu nedenle, önceki içeri aşağıdaki dışarı eşleşir.  
  
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
  
 Sözleşme türü ve sözleşme adı belirtilebilir `Import` daha önce "Temel alır ve dışarı aktarma" bölümünde açıklandığı gibi yavaş bir alma işlemi için öznitelik.  
  
### <a name="prerequisite-imports"></a>Önkoşul İçeri aktarmalar  
 Dışarı aktarılan MEF bölümleri genellikle doğrudan bir istek veya eşleşen bir içeri aktarımı doldurma gerek yanıt olarak bileşim motoru tarafından oluşturulur. Bir bölümü oluştururken, varsayılan olarak, oluşturucu birleşim altyapısı kullanır. Farklı bir oluşturucu kullanın altyapısı yapma ile işaretleyebilirsiniz `ImportingConstructor` özniteliği.  
  
 Her bölümü bileşim motoru tarafından kullanım için yalnızca bir oluşturucuya sahip. Varsayılan oluşturucu yok ve no sağlama `ImportingConstructor` özniteliği veya birden fazla sağlama `ImportingConstructor` öznitelik, bir hata oluşturur.  
  
 İle işaretlenmiş bir oluşturucunun parametrelerini doldurmak için `ImportingConstructor` özniteliği, bu parametrelerin tümü otomatik olarak bildirildiğinden alır. Bu bölümü başlatma sırasında kullanılan içeri aktarmalar bildirmek için kullanışlı bir yoludur. Aşağıdaki sınıf kullanır `ImportingConstructor` alma bildirmek için.  
  
```vb  
Public Class MyClass1  
  
    Private _theAddin As IMyAddin  
  
    'Default constructor will NOT be used  
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
  
    //Default constructor will NOT be  
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
  
 Varsayılan olarak, `ImportingConstructor` özniteliğini kullanır anlaşma türleri ve sözleşme adları tüm parametresi alır. Parametrelerle tasarlayarak bunu geçersiz kılmak mümkündür `Import` anlaşma türü ve sözleşme adı daha sonra açıkça tanımlayabilirsiniz öznitelikleri. Aşağıdaki kod, bir üst sınıf yerine türetilmiş bir sınıf içeri aktarmak için bu söz dizimini kullanır bir oluşturucuyu gösterir.  
  
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
  
 Özellikle, koleksiyon parametrelerle dikkatli olmanız gerekir. Belirtirseniz, örneğin, `ImportingConstructor` türünde bir parametre ile bir oluşturucu üzerinde `IEnumerable<int>`, içe aktarma türü tek bir verme eşleşir `IEnumerable<int>`, dışarı aktarma türü bir dizi yerine `int`. Dışarı aktarımlar türünü eşlemek için `int`, parametresiyle tasarlamanız gerekir `ImportMany` özniteliği.  
  
 İçeri aktarmalar tarafından bildirilen parametreler `ImportingConstructor` özniteliği olarak da işaretlenir *önkoşul alır*. MEF normalde dışarı sağlar ve forma alır bir *döngüsü*. Örneğin, bir döngü nereye nesne A içeri aktarmalar sırayla nesne A. alır B nesne. Normal koşullar altında bir döngü bir sorun değildir ve kapsayıcının hem nesneleri normal olarak oluşturur.  
  
 İçeri aktarılan bir değer bir bölümü oluşturucusu tarafından istendiğinde bu nesne bir döngüde yer alamaz. Nesne A oluşturulması önce o nesnenin B oluşturulmasını gerektiriyorsa, kendisi ve nesne B alır nesne A, sonra döngüsü çözmek mümkün olmayacaktır ve bir birleşim hatası ortaya çıkar. Oluşturucu parametrelerinde bildirilen içeri aktarmalar olan bu nedenle önkoşul içeri aktarmalar, tüm önce doldurulan olmalıdır dışarı gerektirmesi nesne hiçbirini kullanılabilir.  
  
### <a name="optional-imports"></a>İsteğe bağlı içeri aktarmalar  
 `Import` Özniteliği bölümü işlevi için bir gereksinim belirtir. Alma karşılanamazsa, bu bölümün bileşimi başarısız olur ve bölümü kullanılamaz.  
  
 Alma olduğunu belirtebilirsiniz *isteğe bağlı* kullanarak `AllowDefault` özelliği. Bu durumda, bileşim mevcut dışarı eşleşmiyor içe aktarın ve alma özelliği, özellik türü için varsayılan ayarlanmış olsa bile başarılı olur (`null` nesne özelliklerini `false` Boole değerlerini veya sayısal sıfır özellikleri.) Aşağıdaki sınıf isteğe bağlı alma kullanır.  
  
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
  
    //If no matching export is avaliable,  
    //thePlugin will be set to null.  
}  
```  
  
### <a name="importing-multiple-objects"></a>Birden çok nesne içeri aktarma  
 `Import` Özniteliği yalnızca başarıyla oluşan tek bir verme eşleştiğinde. Diğer durumlarda, bir birleşim hatasına neden olur. Aynı anlaşmayla eşleşen birden fazla dışarı aktarmak için kullanın `ImportMany` özniteliği. Bu özniteliği ile işaretlenmiş içeri aktarımlar her zaman isteğe bağlıdır. Örneğin, eşleşen hiçbir dışarı aktarma mevcut olup olmadığını birleşim neden olmaz. Aşağıdaki sınıf herhangi bir sayıda türü dışarı aktarır `IMyAddin`.  
  
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
  
 İçeri aktarılan dizine sıradan kullanarak erişilebilir `IEnumerable<T>` sözdizimi ve yöntem. Sıradan bir dizi kullanmak da mümkündür (`IMyAddin[]`) yerine.  
  
 İle birlikte kullandığınızda bu deseni oldukça önemli olabilir `Lazy<T>` sözdizimi. Kullanarak örneğin, `ImportMany`, `IEnumerable<T>`, ve `Lazy<T>`, istediğiniz sayıda nesne başvuruları dolaylı içe aktarabilir ve yalnızca gerekli olanları örneği. Aşağıdaki sınıf bu deseni gösterir.  
  
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
## <a name="avoiding-discovery"></a>Keşif Önleme  
 Bazı durumlarda, bir katalog bir parçası olarak bulunan bir bölümü önlemek isteyebilirsiniz. Örneğin, bir parçası kaynağından devralındı düşünülen ama kullanılmayan bir temel sınıf olabilir. Bunu yapmanın iki yolu vardır. İlk olarak, kullanabileceğiniz `abstract` bölümü sınıfı anahtar sözcüğü. Bunlardan türeyen sınıflar devralınan dışarı sağlayabilirse soyut sınıflar dışarı aktarmalar, hiçbir zaman sağlar.  
  
 Sınıfı Özet yapılamazsa, kendisiyle tasarlayabilirsiniz `PartNotDiscoverable` özniteliği. Bu öznitelik ile donatılmış bir bölümü hiçbir katalog içine dahil edilmez. Aşağıdaki örnekte bu düzenleri gösterir. `DataOne` katalog tarafından bulunacaktır. Bu yana `DataTwo` olan Özet, onu bulunmaz. Bu yana `DataThree` kullanılan `PartNotDiscoverable` özniteliği değil bulunacaktır.  
  
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
## <a name="metadata-and-metadata-views"></a>Meta veri ve meta veri görünümleri  
 Dışarı aktarma kendileri olarak bilinen hakkında ek bilgiler sağlayabilir *meta verileri*. Meta veri alma bölümü için dışarı aktarılan nesnenin özelliklerini iletmek için kullanılır. İçeri aktarılan bölüm kullanın ya da onu oluşturmak zorunda kalmadan bir dışarı aktarma hakkında bilgi toplamak için aktarır karar vermek için bu verileri kullanabilirsiniz. Bu nedenle, bir içeri aktarma meta veriyi kullanmak için yavaş olması gerekir.  
  
 Meta veri kullanmak için tipik olarak bilinen bir arayüz bildirmelidir bir *meta veri görünümü*, hangi meta verinin kullanılabilir olacağını bildirir. Meta veri görünüm arayüzü yalnızca özelliklere sahip olmalıdır ve bu özellikler içermelidir `get` erişimciler. Bir örnek meta veri görünümü arabirimidir.  
  
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
  
 Bir genel koleksiyon kullanmak da mümkündür `IDictionary<string, object>`, meta veri görünümü ancak bu tür denetlemesi kulanmanız ve kaçınılmalıdır.  
  
 Normalde, meta veri görünümünde adlı özelliklerin tümü gereklidir ve bunları sağlamayan dışarı bir eşleşme dikkate alınmaz. `DefaultValue` Özniteliği belirtir. bir özellik isteğe bağlıdır. Özellik dahil değilse, onu bir parametresi olarak belirtilen varsayılan değeri atanacak `DefaultValue`. Meta verileri ile donatılmış farklı iki sınıf şunlardır: Bu sınıfların her ikisi de önceki meta veri görünümü eşleşir.  
  
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
  
 Meta veri ifade sonra `Export` kullanarak özniteliği `ExportMetadata` özniteliği. Meta veriler her parçasının bir ad/değer çiftinden oluşur. Meta veri adı kısmını meta veri görünümünde uygun özellik adıyla eşleşmelidir ve değeri bu özelliğe atanır.  
  
 Herhangi biri, olacaksa kullanımda hangi meta veri görünümü belirtir içeri Aktarıcı var. Meta veri alma ikinci tür parametre olarak meta veriler arabirimiyle yavaş bir alma bildirilmiş `Lazy<T,T>`. Aşağıdaki sınıf meta verileri önceki bölümüyle içeri aktarır.  
  
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
  
 Çoğu durumda, meta verileri ile birleştirmek istersiniz `ImportMany` kullanılabilir içeri aktarmalar ayrıştırma ve seçin ve yalnızca bir örneği veya belirli bir koşulla eşleşecek şekilde bir koleksiyonu filtrelemek için öznitelik. Aşağıdaki sınıf yalnızca başlatır `IPlugin` nesneleri `Name` "Günlükçü" değeri.  
  
```vb  
Public Class User  
  
    <ImportMany()>  
    Public Property plugins As IEnumerable(Of Lazy(Of IPlugin, IPluginMetadata))  
  
    Public Function InstantiateLogger() As IPlugin  
  
        Dim logger As IPlugin  
        logger = Nothing  
  
        For Each Plugin As Lazy(Of IPlugin, IPluginMetadata) In plugins  
            If (Plugin.Metadata.Name = "Logger") Then  
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
  
    public IPlugin InstantiateLogger ()  
    {  
        IPlugin logger = null;  
  
        foreach (Lazy<IPlugin, IPluginMetadata> plugin in plugins)  
        {  
            if (plugin.Metadata.Name = "Logger") logger = plugin.Value;  
        }  
        return logger;  
    }  
}  
```  
  
<a name="import_and_export_inheritance"></a>   
## <a name="import-and-export-inheritance"></a>İçeri ve dışarı aktarma devralma  
 Bir sınıf bir bölümünden devralıyorsa Bu sınıf ayrıca bir bölümü olabilir. İçeri aktarmalar her zaman alt sınıflar tarafından devralınır. Bu nedenle, bir bölümü öğesinin bir alt her zaman kendi üst sınıfı olarak aynı içeri aktarmalar ile bir parçası olur.  
  
 Dışarı aktarma bildirilen kullanarak `Export` özniteliği olmayan alt sınıflar tarafından devralınır. Ancak, bir kendisini kullanarak dışarı aktarabilir `InheritedExport` özniteliği. Alt sınıfların bölümünün devralır ve sözleşme adı ve sözleşme türü dahil olmak üzere aynı verme sağlayın. Farklı bir `Export` özniteliği `InheritedExport` yalnızca sınıf düzeyinde ve üye düzeyinde uygulanabilir. Bu nedenle, hiçbir zaman üye düzeyi dışarı devralınabilir.  
  
 Aşağıdaki dört sınıfları alma ilkeleri göstermek ve devralma verin. `NumTwo` öğesinden devralınan `NumOne`, bu nedenle `NumTwo` alacak `IMyData`. Sıradan dışarı devralınmaz, bu nedenle `NumTwo` herhangi bir şey aktarmaz. `NumFour` öğesinden devralınan `NumThree`. Çünkü `NumThree` kullanılan `InheritedExport`, `NumFour` sözleşme türüne sahip bir dışa aktarma sahip `NumThree`. Üye düzeyi dışarı hiçbir zaman devralınan, bu nedenle `IMyData` aktarılmaz.  
  
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
  
 İle ilişkili meta veri varsa bir `InheritedExport` özniteliği, bu meta veri de devralınır. (Daha fazla bilgi için önceki "Meta veri ve meta veri görünümleri" bölümüne bakın.) Devralınan meta alt sınıf tarafından değiştirilemez. Ancak, ile yeniden bildirerek `InheritedExport` özniteliğinin anlaşma türü ve aynı sözleşme adı ile ancak yeni meta veriler, alt sınıf yeni meta veri ile devralınan meta değiştirebilirsiniz. Aşağıdaki sınıf Bu ilkeyi gösterir. `MegaLogger` Bölümü devraldığı `Logger` ve içerir `InheritedExport` özniteliği. Bu yana `MegaLogger` durum adlı tekrar bildirdiğinden yeni meta devralmaz adı ve sürümü meta verileri `Logger`.  
  
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
  
 Yeniden bildirirken `InheritedExport` özniteliği meta veriyi geçersiz kılmak için anlaşma türleri aynı olduğundan emin olun. (Önceki örnekte, `IPlugin` sözleşme türüdür.) Bunlar, geçersiz kılma yerine farklıysa ikinci öznitelik ikinci, bağımsız bir verme bölümünden oluşturun. Genellikle, bu, geçersiz kıldığınızda anlaşma türünü açıkça belirtmek olacağı anlamına gelir bir `InheritedExport` özniteliği, önceki örnekte gösterildiği gibi.  
  
 Arabirimleri doğrudan başlatılamaz olduğundan, bunlar genellikle ile tasarlanır `Export` veya `Import` öznitelikleri. Ancak, bir arabirim ile tasarlanabilir bir `InheritedExport` özniteliği arabirimi düzeyinde ve ilişkili meta verileri dışarı aktarma herhangi yanı sıra tüm sınıflar tarafından devralınır. Arabirim ancak bir parçası olarak kullanılabilir olmaz.  
  
<a name="custom_export_attributes"></a>   
## <a name="custom-export-attributes"></a>Özel dışarı aktarım öznitelikleri  
 Temel dışarı aktarım öznitelikleri `Export` ve `InheritedExport`, meta verileri öznitelik özellikleri olarak eklemek için genişletilebilir. Bu teknik benzer meta verileri birçok bölüme uygulamak veya meta veri özniteliklerinin kalıtım ağacını oluşturmak için kullanışlıdır.  
  
 Özel bir öznitelik anlaşma türü, sözleşme adı veya diğer meta verileri belirtebilirsiniz. İçinden devralma sınıfı özel bir öznitelik tanımlamak için `ExportAttribute` (veya `InheritedExportAttribute`) ile tasarlanmalıdır `MetadataAttribute` özniteliği. Aşağıdaki sınıf özel bir öznitelik tanımlar.  
  
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
  
 Bu sınıf adlı özel bir öznitelik tanımlar `MyAttribute` sözleşme türüyle `IMyData` ve adlı bazı meta verileri `MyMetadata`. Bir sınıftaki tüm özellikler işaretlenmiş `MetadataAttribute` özniteliği özel özniteliğinde tanımlanan meta veriler olarak kabul edilir. Aşağıdaki iki bildirim eşdeğerdir.  
  
```vb  
<Export(GetType(IMyAddin))>  
<ExportMetadata("MyMetadata", "theData")>  
Public Property myAddin As MyAddin  
  
<MyAttribute("theData")>  
Public Property myAddin As MyAddin  
```  
  
```csharp  
[Export(typeof(IMyAddin)),   
    ExportMetadata("MyMetadata", "theData")]  
public MyAddin myAddin { get; set; }  
```  
  
```  
[MyAttribute("theData")]  
public MyAddin myAddin { get; set; }  
```  
  
 İlk bildiriminde sözleşme türü ve meta veriler açık olarak tanımlanır. İkinci bildiriminde anlaşma türü ve meta veri özelleştirilmiş özniteliğinde örtük. Aynı meta verilerinin büyük bir miktarını birçok bölümleri (örneğin, yazar veya telif hakkı bilgileri) burada uygulanması gereken durumlarda özellikle çok fazla zaman ve çoğaltma özel bir öznitelik kullanarak kaydedebilirsiniz. Ayrıca, özel özniteliklerin kalıtım ağaçları farklılıklara izin vermek için oluşturulabilir.  
  
 İsteğe bağlı meta veriler özel bir öznitelik oluşturmak için kullanabileceğiniz `DefaultValue` özniteliği. Bu öznitelik, bir özel öznitelik sınıftaki bir özelliğe uygulandığında düzenlenmiş özellik isteğe bağlıdır ve bir dışarı aktarma tarafından sağlanması gerekmez belirtir. Özelliği için bir değer sağlanmazsa, bu özellik türü için varsayılan değer atanacak (genellikle `null`, `false`, ya da 0.)  
  
<a name="creation_policies"></a>   
## <a name="creation-policies"></a>Oluşturma ilkeleri  
 Bir bölümü bir içeri aktarma ve birleşim gerçekleştirildiğinde, kapsayıcının eşleşen bir dışarı aktarım bulmaya çalışır. Bir verme içeri aktarmaya başarıyla eşleşirse, içeri aktarma üye dışarı aktarılan nesnenin örneğine ayarlanır. Bu örnek nereden geldiğini dışarı aktarılan bölümün tarafından denetlenir *oluşturma ilkesi*.  
  
 İki olası oluşturma ilke *paylaşılan* ve *paylaşılmayan*. Bir parçası oluşturma ilkesi ile paylaşılan sözleşme sahip bir bölüm için kapsayıcıdaki her içeri aktarma arasında paylaştırılır. Bileşim motoru bir eşleşme bulur ve içeri aktarma özelliğini ayarlamak sahip olduğunda yalnızca bir zaten mevcut değilse yeni bir kopya bölümünün örneği; Aksi takdirde, varolan kopyayı kullanacaksınız. Bu, birçok nesne başvuruları aynı bölüm için olabileceği anlamına gelir. Bu tür bölümleri birçok yerden değiştirilebilir iç durumu güvenmemelisiniz. Bu ilke, statik bölümleri, hizmetler sağlayan bölümler ve çok miktarda bellek veya diğer kaynakları tüketen bölümleri için uygundur.  
  
 Eşleşen bir içeri aktarma, dışarı aktarma biri için bulunan her zaman bir parçası oluşturma ilkesiyle paylaşılmayan oluşturulur. Yeni bir kopyasını, bu nedenle bölümün dışarı aktarılan sözleşmeleri biriyle eşleşen kapsayıcıdaki her bir içeri aktarma için oluşturulacak. Bu kopyalar iç durumu paylaşılmaz. Bu ilke, burada her alma iç durumuna ihtiyaç duyduğu bölümler için uygundur.  
  
 İçeri aktarma ve dışarı aktarma değerlerinden bir bölümün oluşturma ilkesi belirleyebilirsiniz `Shared`, `NonShared`, veya `Any`. Varsayılan değer `Any` her ikisi için alır ve verir. Belirleyen bir dışarı aktarım `Shared` veya `NonShared` yalnızca aynısını belirten ya da belirten bir içeri aktarma ile eşleşir `Any`. Benzer şekilde, belirten alma `Shared` veya `NonShared` yalnızca aynısını belirten ya da belirten bir dışarı aktarma ile eşleşir `Any`. İçeri ve dışarı aktarmalar uyumsuz oluşturma ilkeleri ile bir eşleşme bir içeri aktarma ve dışarı aktarma, sözleşme adı veya sözleşme türü bir eşleşme olmayan aynı şekilde dikkate alınmaz. İçeri ve dışarı aktarma belirtirseniz, `Any`, değil oluşturma ilkesi belirtin veya varsayılan `Any`, oluşturma ilkesi paylaşılan varsayılan olur.  
  
 Aşağıdaki örnek, içeri ve dışarı aktarma oluşturma ilkeleri belirtme gösterir. `PartOne` Varsayılan değer olacak şekilde bir oluşturma ilkesi belirtmiyor `Any`. `PartTwo` Varsayılan değer olacak şekilde bir oluşturma ilkesi belirtmiyor `Any`. Her ikisi de içeri ve varsayılan olarak dışarı aktarma beri `Any`, `PartOne` paylaşılır. `PartThree` belirten bir `Shared` oluşturma ilkesi, bu nedenle `PartTwo` ve `PartThree` aynı kopyasını paylaşır `PartOne`. `PartFour` belirten bir `NonShared` oluşturma ilkesi, bu nedenle `PartFour` içinde paylaşılmayan olacaktır `PartFive`. `PartSix` belirten bir `NonShared` oluşturma ilkesi. `PartFive` ve `PartSix` her ayrı kopyası alacak `PartFour`. `PartSeven` belirten bir `Shared` oluşturma ilkesi. Olduğundan dışarı aktarılan `PartFour` oluşturma ilkesi ile `Shared`, `PartSeven` alma şeyle eşleşmez ve doldurulmaz.  
  
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
    'Since the export's creation policy was explictly  
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
    //Since the export's creation policy was explictly  
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
## <a name="life-cycle-and-disposing"></a>Yaşam döngüsü ve atma  
 Bölümleri bileşim kapsayıcıda barındırıldığından, yaşam döngüsü sıradan nesnelerden daha karmaşık olabilir. Bölümleri iki önemli yaşam döngüsü ile ilgili arabirimler uygulayabilirsiniz: `IDisposable` ve `IPartImportsSatisfiedNotification`.  
  
 Kapatma sırasında aşağı yapılması iş gerektiren veya kaynakları serbest bırakmak gereken bölümleri uygulamanız gerekir `IDisposable`, .NET Framework nesneleri için normal. Ancak, kapsayıcıyı oluşturur ve bölümlere referanslar bulundurur olduğundan, yalnızca bir bölüm kapsayıcı çağırmalıdır `Dispose` yöntemini. Kapsayıcı uygulayan `IDisposable`ve kendi temizleme bölümü olarak `Dispose` çağırır `Dispose` sahip olduğu tüm bölümleri. Ve sahip olduğu tüm parçaları artık gerekli değildir, bu nedenle, her zaman kapsayıcının silmesi gerekir.  
  
 Uzun dönemli bileşim kapsayıcılar için paylaşılmayan oluşturma ilkesi ile bölümleri bellek tüketimi bir sorun olabilir. Paylaşılmayan bölümleri birden çok kez oluşturulabilir ve kapsayıcı bırakılana kadar silinecek değil. Bu işlem için kapsayıcı sağlar `ReleaseExport` yöntemi. Paylaşılmayan bir dışarı aktarma üzerinde bu yöntemi çağırmadan birleşim kapsayıcıdan bu dışarı kaldırır ve siler. Yalnızca ağaç aşağı ve benzeri kaldırılan dışarı aktarım tarafından kullanılan bölümleri da kaldırılır ve atıldı. Bu şekilde, kapsayıcının kendisini atma olmadan kaynakları istenemiyor.  
  
 `IPartImportsSatisfiedNotification` adlı bir yöntem içerir `OnImportsSatisfied`. Bu yöntem, kapsayıcının birleşim tamamlandı ve bölümünün içeri aktarmalar kullanıma hazır olduğunda arabirimini uygulayan tüm bölümleri tarafından çağrılır. Bölümleri diğer bölümleri Imports doldurmak için bileşim motoru tarafından oluşturulur. İçeri aktarmalar bir bölümü ayarlamadan önce dayanan veya bu değerleri kullanarak önkoşul olarak belirtilmiş sürece bölüm oluşturucusu içerisinde içeri aktarılan değerlerini işleyen hiçbir başlangıç gerçekleştiremezsiniz `ImportingConstructor` özniteliği. Bu genellikle tercih edilen yöntemdir, ancak bazı durumlarda Oluşturucu ekleme kullanılamayabilir. Bu gibi durumlarda başlatma gerçekleştirilebilecek `OnImportsSatisfied`, ve bölümü uygulamalıdır `IPartImportsSatisfiedNotification`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kanal 9 Video: Yönetilen Genişletilebilirlik Çerçevesi uygulamalarınızla açın](http://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)  
 [Kanal 9 Video: Yönetilen Genişletilebilirlik Çerçevesi (MEF) 2.0](http://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)
