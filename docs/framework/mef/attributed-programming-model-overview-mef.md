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
ms.openlocfilehash: 5429dfbf7b318b60d6c3150315dbe22ee73b4792
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563450"
---
# <a name="attributed-programming-model-overview-mef"></a>Öznitelikli Programlama Modeline Genel Bakış (MEF)
İçinde Yönetilen Genişletilebilirlik Çerçevesi (MEF), bir *programlama modeli* MEF çalıştığı kavramsal nesne kümesini tanımlayan belirli bir yöntemdir. Kavramsal bu nesneler, bölümleri, içeri aktarmalar ve dışarı aktarmaları içerir. MEF bu nesneleri kullanan, ancak nasıl temsil belirtmiyor. Bu nedenle, çok çeşitli programlama modellerini programlama modelleri de dahil olmak üzere özelleştirilmiş mümkün.  
  
 MEF kullanılan programlama modeli varsayılan *öznitelikli programlama modeli*. Öznitelikli Programlama modeli bölümleri, sıradan bir .NET Framework sınıf süslemek özniteliklerle içeri aktarmalar, dışarı aktarma ve diğer nesneleri tanımlanır. Bu konuda, bir MEF uygulaması oluşturmak için öznitelikli programlama modeli tarafından sağlanan özniteliklerin kullanmayı açıklar.  
  
<a name="import_and_export_basics"></a>   
## <a name="import-and-export-basics"></a>İçeri ve dışarı aktarma temelleri  
 Bir *dışarı* diğer bölümlerinde kapsayıcı bir bölümü sağlayan bir değerdir ve *alma* erişilebilir dışarı doldurulması kapsayıcıya, bir bölümü ifade bir gereksinimdir. Öznitelikli programlama modelinde, içeri ve dışarı aktarmalar sınıfları ve üyeleri ile tasarlayarak bildirilen `Import` ve `Export` öznitelikleri. `Export` Özniteliği donatmak bir sınıf, alan, özelliği veya yöntemi sırasında `Import` öznitelik, bir alan, özelliği veya Oluşturucu parametresi süslemek.  
  
 Bir dışarı aktarma ile eşleştirilecek bir içeri aktarma, içeri ve dışarı aktarma aynı olması gerekir *sözleşme*. Anlaşma adı verilen bir dizenin oluşur *sözleşme adı*ve adlı dışarı aktarılan veya içeri aktarılan nesnenin türü *sözleşme türü*. Yalnızca sözleşme adı ve sözleşme türü eşleşmesi durumunda bir dışarı aktarma belirli bir içeri aktarma yerine getirmek için değerlendirilir.  
  
 Sözleşme parametrelerinin her ikisini ya da örtük veya açık olabilir. Aşağıdaki kod, temel bir içeri aktarma bildiren bir sınıfı gösterir.  
  
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
  
 Bu içeri aktarma `Import` özniteliğine sahip bir sözleşme türü ya da bağlı bir sözleşme adı parametresi. Bu nedenle, her ikisi de düzenlenmiş özellikten. Bu durumda, sözleşme türü olacaktır `IMyAddin`, ve anlaşma türü ile oluşturulan benzersiz bir dize sözleşme adı olacaktır. (Diğer bir deyişle, yalnızca, adları da türünden çıkarsanan dışarı aktarmaları sözleşme adı eşleşir `IMyAddin`.)  
  
 Önceki alma eşleşen bir dışarı aktarma gösterir.  
  
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
  
 Sözleşme türü bu dışarı aktarma, `IMyAddin` bir parametresi olarak belirtildiğinden `Export` özniteliği. Dışarı aktarılan tür ya da aynı anlaşma türü olması gerekir, Sözleşme türünden türetilmesi veya sözleşme türü bir arabirim ise uygulama. Bu dışarı aktarma, gerçek tür içinde `MyLogger` arabirimi uygulayan `IMyAddin`. Sözleşme adı, bu dışarı aktarma önceki alma eşleştiğini anlamına gelir. anlaşma türü ile algılanır.  
  
> [!NOTE]
>  Dışarı ve içeri aktarmalar, genel bir sınıf veya üye üzerinde bildirilmelidir. Diğer bildirimler desteklenir, ancak dışarı aktarma veya özel bir içeri aktarma, korumalı veya iç üye bölümü ayırma modeli ayırır ve bu nedenle önerilmez.  
  
 Sözleşme türü dışarı ve içeri aktarma için bir eşleşme olarak kabul edilmesi için tam olarak eşleşmelidir. Aşağıdaki dışa aktarım göz önünde bulundurun.  
  
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
  
 Sözleşme türü bu dışarı aktarma, `MyLogger` yerine `IMyAddin`. Olsa da `MyLogger` uygulayan `IMyAddin`ve bu nedenle dönüştürülebilir bir `IMyAddin` nesnesi, bu dışarı aktarma anlaşması türleri aynı olmadığından önceki alma eşleşmez.  
  
 Genel olarak, sözleşme adı belirtmeniz gerekli değildir ve anlaşma türü ve meta verileri açısından çoğu sözleşmeleri tanımlanması gerekir. Ancak, belirli koşullar altında doğrudan sözleşme adı belirtmek önemlidir. Bir sınıf temelleri gibi bir ortak türü değerlerden verdiğinde en yaygın bir durumdur. Sözleşme adı, ilk parametresi olarak belirtilebilir `Import` veya `Export` özniteliği. Aşağıdaki kod, alma ve verme belirtilen sözleşme adıyla gösterir `MajorRevision`.  
  
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
  
 Sözleşme türü belirtilmediği takdirde, yine de içeri veya dışarı aktarmayı türünden çıkarılabilir olacaktır. Ancak, sözleşme adı açıkça belirtilmiş olsa bile, sözleşme türü de içeri aktarma ve bir eşleşme olarak kabul edilmesi için dışarı aktarma için tam olarak eşleşmelidir. Örneğin, varsa `MajorRevision` alan bir dize olan, çıkarsanan anlaşması türleri eşleşmiyor ve dışarı aktarma, alma, aynı sözleşme adına sahip olmasına rağmen aynı olmamalıdır.  
  
### <a name="importing-and-exporting-a-method"></a>İçeri ve dışarı aktarma yöntemi  
 `Export` Özniteliği de tasarlamanız bir yöntem bir sınıf, özellik veya işlev aynı şekilde. Türü çıkarsanamıyor olarak yöntemi dışarı bir sözleşme türü veya sözleşme adı belirtmeniz gerekir. Belirtilen tür gibi özel bir temsilci ya da genel bir tür olabilir `Func`. Aşağıdaki sınıf adlı bir yöntem dışarı aktarır `DoSomething`.  
  
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
  
 Bu sınıftaki `DoSomething` yöntemi tek bir alan `int` parametresi ve döndürür bir `string`. Bu dışarı aktarma eşleştirmek için içeri aktarma bölümü uygun bir üye bildirmeniz gerekir. Sınıfına aşağıdaki içeri aktarmaları `DoSomething` yöntemi.  
  
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
  
 Nasıl kullanıldığı hakkında daha fazla bilgi için `Func<T, T>` nesne, bkz: <xref:System.Func%602>.  
  
<a name="types_of_imports"></a>   
## <a name="types-of-imports"></a>İçeri aktarmalar türleri  
 Yavaş, gerekli ve isteğe bağlı dinamik dahil olmak üzere birkaç içeri aktarma, MEF destek türleri.  
  
### <a name="dynamic-imports"></a>Dinamik içeri aktarmalar  
 Bazı durumlarda, içeri aktarma sınıfı sözleşmeye ada sahip dışarı aktarma herhangi bir türde eşleşen isteyebilirsiniz. Bu senaryoda sınıf bildirebilir bir *dinamik içeri aktarma*. Aşağıdaki içeri aktarma, hiçbir dışarı aktarma sözleşme adı "Width" ile eşleşir.  
  
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
  
 Ne zaman anlaşma türü çıkarılan gelen `dynamic` anahtar sözcüğü, herhangi bir sözleşme türü eşleşir. Bu durumda, bir içeri aktarma gereken **her zaman** eşleştirmek için bir sözleşme adı belirtin. (Hiçbir sözleşme adı belirtilmezse, içeri aktarma hiçbir dışarı eşleşecek şekilde kabul edilir.) Aşağıdaki dışarı aktarmaları her ikisi de önceki alma eşleşir.  
  
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
  
 Kuşkusuz, içeri aktarma sınıfı rastgele türünde bir nesne ile dağıtılacak hazırlanmalıdır.  
  
### <a name="lazy-imports"></a>İçeri aktarmaları  
 Nesneyi hemen oluşturulmadı, bazı durumlarda, içeri aktarılan nesneye dolaylı bir başvuru alma sınıfı gerektirebilir. Bu senaryoda sınıf bildirebilir bir *yavaş alma* anlaşma türünü kullanarak `Lazy<T>`. Aşağıdaki içeri aktarma özelliği, yavaş bir içeri aktarma bildirir.  
  
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
  
 Bakış açısıyla bileşim motoru, bir sözleşme türü `Lazy<T>` anlaşma türü ile aynı olarak kabul edilir `T`. Bu nedenle, önceki alma aşağıdaki dışa aktarım eşleşir.  
  
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
  
 Sözleşme adı ve anlaşma türü belirtilebilir `Import` "Temel alır ve dışarı aktarma" bölümünde daha önce açıklandığı gibi yavaş bir alma işlemi için özniteliği.  
  
### <a name="prerequisite-imports"></a>Önkoşul İçeri aktarmalar  
 Dışarı aktarılan MEF bölümleri genellikle yanıt olarak doğrudan bir istek veya eşleşen bir içeri aktarma doldurmak için gereken bileşim motoru tarafından oluşturulur. Bir bölüm oluşturulduğunda varsayılan olarak, parametresiz oluşturucuya bileşim motoru kullanır. Farklı bir oluşturucu kullanın altyapısı sağlamak için birlikte işaretleyebilirsiniz `ImportingConstructor` özniteliği.  
  
 Yalnızca bir yapıcısı bileşim motoru tarafından kullanılmak üzere her bir bölümü olabilir. Varsayılan oluşturucu yok ve Hayır sağlayarak `ImportingConstructor` özniteliği veya birden fazla sağlama `ImportingConstructor` öznitelik, bir hata üretecektir.  
  
 İşaretli bir oluşturucuda parametrelerinin doldurmak için `ImportingConstructor` özniteliği, tüm bu parametreler otomatik olarak bildirilir alır. Bu bölümü başlatma sırasında kullanılan içeri aktarmalar bildirmek için kullanışlı bir yoldur. Aşağıdaki sınıf kullandığı `ImportingConstructor` alma bildirmek için.  
  
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
  
 Varsayılan olarak, `ImportingConstructor` özniteliğini kullanır anlaşması türleri ve sözleşme adları tüm parametre alır. Parametrelerle tasarlayarak bunu geçersiz kılmak mümkündür `Import` öznitelikleri, sözleşme adı ve anlaşma türü daha sonra açıkça tanımlayabilirsiniz. Aşağıdaki kod, bir üst sınıf yerine türetilmiş bir sınıf içeri aktarmak için şu söz dizimini kullanan bir oluşturucuyu gösterir.  
  
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
  
 Özellikle, koleksiyon parametrelerle dikkatli olmanız gerekir. Örneğin belirtirseniz, `ImportingConstructor` türünde bir parametreye sahip bir Oluşturucuda `IEnumerable<int>`, içeri aktarma türünde tek bir dışarı aktarım eşleşecektir `IEnumerable<int>`, dışarı aktarma türü bir dizi yerine `int`. Bir dışarı aktarma türü eşleşecek şekilde `int`, parametresiyle donatmak sahip olduğunuz `ImportMany` özniteliği.  
  
 Alınanlar tarafından bildirilen parametreler `ImportingConstructor` özniteliği olarak da işaretlenir *önkoşul aktarır*. MEF normalde dışarı aktarmaları sağlar ve forma alır bir *döngüsü*. Örneğin, bir döngü nesne A içeri aktarmalar sırayla nesne A. aktarır B, nesne olur. Normal koşullar altında bir döngü bir sorun değildir ve kapsayıcının normalde iki nesneleri oluşturur.  
  
 Bir bölüm Oluşturucu tarafından içeri aktarılan bir değer gerektiğinde, o nesnenin bir döngü alamaz. Nesne A B Bu nesne, oluşturduğu önce oluşturulmasını gerektiriyorsa, kendisi ve nesne B alır nesne A, sonra döngüsü çözemez ve bir birleştirme hatası meydana gelir. İçeri aktarmalar Oluşturucu parametrelere bildirilen olan bu nedenle önkoşul alır, tüm önce doldurulmalıdır herhangi dışarı gerektirdiği nesne kullanılabilir.  
  
### <a name="optional-imports"></a>İsteğe bağlı içeri aktarmalar  
 `Import` Özniteliği bölümü işlevi için bir gereksinim belirtir. Bir içeri aktarma yerine getirilemiyor, bu bölümü olarak başarısız olur ve bölümü kullanılabilir olmaz.  
  
 Bir içeri aktarma olduğunu belirtebilirsiniz *isteğe bağlı* kullanarak `AllowDefault` özelliği. Bu durumda, bileşim alma mevcut dışarı eşleşmiyor ve içeri aktarma özelliği, kendi özellik türü için varsayılan ayarlanacak bile başarılı olur (`null` nesne özelliklerini `false` Boole değerlerini veya sayısal sıfır Özellikler.) Aşağıdaki sınıf isteğe bağlı bir içeri aktarma kullanır.  
  
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
  
### <a name="importing-multiple-objects"></a>Birden çok nesne alma  
 `Import` Özniteliği yalnızca başarıyla oluşan bir ve yalnızca bir dışarı aktarma eşleştiğinde. Diğer durumlarda, bir birleştirme hatası oluşturur. Aynı anlaşmaya eşleşen birden fazla dışarı aktarmak için kullanın `ImportMany` özniteliği. İçeri aktarmalar bu özniteliği ile işaretlenmiş her zaman isteğe bağlıdır. Örneğin, eşleşen dışarı aktarımlar mevcut değilse birleştirme başarısız olmaz. Aşağıdaki sınıf herhangi bir sayıda tür dışarı aktarır `IMyAddin`.  
  
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
  
 İçeri aktarılan dizi sıradan kullanarak erişilebilir `IEnumerable<T>` sözdizimi ve yöntem. Bir sıradan dizi kullanmak da mümkündür (`IMyAddin[]`) bunun yerine.  
  
 İle birlikte kullandığınızda bu desen çok önemli olabilir `Lazy<T>` söz dizimi. Kullanarak örneğin, `ImportMany`, `IEnumerable<T>`, ve `Lazy<T>`, istediğiniz sayıda nesne dolaylı başvuru içeri aktarabilir ve yalnızca gerekli olanları örneği. Bu düzen aşağıdaki sınıfı gösterir.  
  
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
 Bazı durumlarda, bir katalog bir parçası olarak bulunan bir bölümünün engellemek isteyebilirsiniz. Örneğin, parça öğesinden devralındı amaçlandı, ancak kullanılmayan bir temel sınıf olabilir. Bunu yapmanın iki yolu vardır. İlk olarak kullanabileceğiniz `abstract` bölümü sınıfı anahtar sözcüğü. Devralınan dışarı aktarımlar sınıfları sağlasa soyut sınıfları dışarı aktarma, hiçbir zaman sağlar.  
  
 Sınıfı soyut olarak yapılamaz, kendisiyle tasarlayabilirsiniz `PartNotDiscoverable` özniteliği. Bu özniteliği ile donatılmış bir bölümü herhangi bir katalogda dahil edilmez. Aşağıdaki örnek, bu desenleri gösterir. `DataOne` katalog tarafından bulunacaktır. Bu yana `DataTwo` olan soyut, bu bulunmaz. Bu yana `DataThree` kullanılan `PartNotDiscoverable` özniteliği, bu bulunmaz.  
  
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
## <a name="metadata-and-metadata-views"></a>Meta verileri ve meta veri görünümleri  
 Dışarı aktarmalar kendileri olarak bilinen hakkında ek bilgiler sağlayabilir *meta verileri*. Meta verileri içeri aktarma bölümü dışarı aktarılan nesnenin özelliklerini belirtmek için kullanılabilir. İçeri aktarma bölümünü kullanın veya bu oluşturmak zorunda kalmadan bir dışarı aktarma hakkında bilgi toplamak için dışarı aktarır karar vermek için bu verileri kullanabilirsiniz. Bu nedenle, bir içeri aktarma meta verileri kullanmak için yavaş olması gerekir.  
  
 Meta veri kullanmak için tipik olarak bilinen bir arabirim bildirmelidir bir *meta veri görünümü*, hangi meta verileri kullanıma sunulacak bildirir. Meta veri görünümü arabirimi yalnızca özelliklere sahip olması gerekir ve bu özelliklere sahip olması gerekir `get` erişimcileri. Aşağıdaki örnek bir meta veri görünümü arabirimidir.  
  
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
  
 Bir genel koleksiyon kullanmak da mümkündür `IDictionary<string, object>`olarak meta veri görünümü, ancak bu tür denetimi kulanmanız ve kaçınılmalıdır.  
  
 Normalde, gerekli olan tüm meta veri görünümü'nde adlı özellikleri ve bunları sağlamayan hiçbir dışarı aktarma işlemini bir eşleşme değerlendirilmeyecek. `DefaultValue` Özniteliği, bir özelliğin isteğe bağlı olduğunu belirtir. Özellik dahil edilmezse, bir parametre olarak belirtilen varsayılan değerin atanacak `DefaultValue`. Meta veri ile tasarlanmış iki farklı sınıfları şunlardır: Bu sınıfların her ikisi de önceki meta veri görünümü eşleşir.  
  
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
  
 Meta veri sonra ifade edilir `Export` kullanarak özniteliği `ExportMetadata` özniteliği. Her bir meta veri parçası bir ad/değer çiftinden oluşur. Meta veri adı kısmı meta veri görünümü'nde uygun özellik adıyla eşleşmelidir ve değeri, bu özelliğe atanır.  
  
 Herhangi biri, olacaksa kullanımda hangi meta veri görünümü belirten alıcısı var. Meta veri alma ikinci tür parametresi olarak meta veriler arabirimi ile yavaş bir içeri aktarma bildirilmiş `Lazy<T,T>`. Aşağıdaki sınıf önceki bölümünde meta verilerle içeri aktarır.  
  
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
  
 Çoğu durumda, meta verilerle birleştirmek istersiniz `ImportMany` kullanılabilir Imports ayrıştırmak ve seçin ve yalnızca bir örneği veya belirli bir koşulla eşleşecek şekilde bir koleksiyonu filtrelemek için özniteliği. Aşağıdaki sınıf yalnızca başlatır `IPlugin` sahip nesneleri `Name` "Günlükçüsü" değeri.  
  
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
## <a name="import-and-export-inheritance"></a>İçeri ve dışarı aktarma devralma  
 Bir sınıf bir bölümünden devralınırsa, bu sınıf ayrıca bir bölümü olabilir. İçeri aktarmalar her zaman alt sınıflar tarafından devralınır. Bu nedenle, bir parça öğesinin her zaman üst sınıfıyla aynı Alınanlarla bir parçası olur.  
  
 Dışarı aktarmalar kullanarak bildirilen `Export` özniteliği alt sınıflar tarafından devralınmaz. Ancak, bir kendisini kullanarak dışarı aktarabilir `InheritedExport` özniteliği. Adornerset'in alt bölümü devralır ve sözleşme adı ve anlaşma türü de dahil olmak üzere aynı dışarı aktarma da sağlar. Farklı bir `Export` özniteliği `InheritedExport` yalnızca sınıf düzeyinde ve üye düzeyinde uygulanabilir. Bu nedenle, hiçbir üye düzeyinde dışarı aktarmaları devralınabilir.  
  
 Aşağıdaki dört sınıflar, içeri aktarma sürecin prensiplerini göstermek ve devralma dışarı aktarın. `NumTwo` devralınan `NumOne`, bu nedenle `NumTwo` içeri aktaracak `IMyData`. Sıradan dışarı aktarmaları devralınmaz, bu nedenle `NumTwo` herhangi bir şey aktarmaz. `NumFour` devralınan `NumThree`. Çünkü `NumThree` kullanılan `InheritedExport`, `NumFour` sözleşme türü ile bir dışarı aktarma yok `NumThree`. Üye düzeyinde dışarı aktarmaları hiçbir zaman devralınır, bu nedenle `IMyData` aktarılmaz.  
  
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
  
 İle ilişkili meta veri varsa bir `InheritedExport` özniteliği, bu meta verileri de devralınır. (Daha fazla bilgi için önceki "Meta verileri ve meta veri görünümleri" bölümüne bakın.) Alt sınıf tarafından devralınan meta verileri değiştirilemez. Ancak, yeniden bildirme tarafından `InheritedExport` özniteliği aynı anlaşma ve sözleşme yazın, ancak yeni meta veriler, alt sınıfın yeni meta verileriyle devralınan meta verileri değiştirebilirsiniz. Aşağıdaki sınıf, bu ilkeyi gösterir. `MegaLogger` Bölümü devraldığı `Logger` ve içerir `InheritedExport` özniteliği. Bu yana `MegaLogger` durumu adlı yeniden bildirir yeni meta devralmaz adı ve sürümü meta verilerine `Logger`.  
  
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
  
 Yeniden bildirirken `InheritedExport` öznitelik meta verileri geçersiz kılma, anlaşması türleri aynı olduğundan emin olun. (Önceki örnekte, `IPlugin` anlaşma türü.) İkinci öznitelik bunlar geçersiz kılmak yerine, farklıysa ikinci bağımsız bir dışarı aktarma bölümünden oluşturacaksınız. Genellikle, bu sözleşme türü, geçersiz kıldığınızda açıkça belirtmek olacağı anlamına gelir bir `InheritedExport` , önceki örnekte gösterildiği gibi öznitelik.  
  
 Arabirimler doğrudan oluşturulamaz olduğundan, bunlar genellikle ile donatılmış olmalıdır olamaz `Export` veya `Import` öznitelikleri. Ancak, bir arabirim ile tasarlanabilir bir `InheritedExport` özniteliği arabirim düzeyinde ve dışarı aktarma herhangi yanı sıra meta veri ilişkili tüm sınıflar tarafından devralınır. Bir parçası olarak, ancak arabirim kullanılamaz.  
  
<a name="custom_export_attributes"></a>   
## <a name="custom-export-attributes"></a>Özel dışarı aktarma öznitelikleri  
 Temel dışarı aktarma öznitelik `Export` ve `InheritedExport`, meta veri öznitelik özellikleri içerecek şekilde genişletilebilir. Bu teknik, birçok bölüme benzer meta veri uygulamak veya meta veri öznitelikleri, bir devralma ağacı oluşturma için kullanışlıdır.  
  
 Sözleşme türü, sözleşme adı veya diğer meta verileri özel bir öznitelik belirtebilirsiniz. Özel bir öznitelik öğesinden devralan bir sınıf tanımlamak için `ExportAttribute` (veya `InheritedExportAttribute`) ile belirtilmiş olmalıdır `MetadataAttribute` özniteliği. Aşağıdaki sınıf özel bir öznitelik tanımlar.  
  
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
  
 Bu sınıf adlı özel bir öznitelik tanımlar `MyAttribute` sözleşme türüyle `IMyData` ve bazı meta veriler adlı `MyMetadata`. Bir sınıftaki tüm özellikler ile işaretlenen `MetadataAttribute` özniteliği özel özniteliğinde tanımlanan meta veriler olarak kabul edilir. Aşağıdaki iki bildirimi eşdeğerdir.  
  
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
  
 İlk bildiriminde sözleşme türü ve meta verileri açıkça tanımlanır. İkinci bildiriminde anlaşma türü ve meta veri özelleştirilmiş özniteliğinde örtüktür. Burada aynı meta verilerinin büyük bir miktarını birçok bölümü (örneğin, yazar veya telif hakkı bilgileri) uygulanması gereken durumlarda özellikle çok fazla zaman ve çoğaltma özel özniteliğini kullanarak kaydedebilirsiniz. Daha fazla özel özniteliklerin devralma ağacı farklılıklara izin vermek oluşturulabilir.  
  
 İsteğe bağlı meta veri özel bir öznitelik oluşturmak için kullanabileceğiniz `DefaultValue` özniteliği. Bu öznitelik, bir özel öznitelik sınıftaki bir özelliğe uygulandığında, düzenlenmiş özellik isteğe bağlıdır ve bir dışarı Aktarıcı tarafından sağlanması gerekmez belirtir. Özellik için bir değer sağlanmazsa, bu özellik türü için varsayılan değer atanır (genellikle `null`, `false`, veya 0.)  
  
<a name="creation_policies"></a>   
## <a name="creation-policies"></a>İlkeleri oluşturma  
 Bir bölümü bir içeri aktarma ve oluşturma işlemi gerçekleştirildiğinde belirttiğinde, kapsayıcının eşleşen bir dışarı aktarım bulmaya çalışır. Bir dışarı aktarma ile içeri aktarma başarıyla eşleşirse, içeri aktarma üye dışarı aktarılan nesne örneğine ayarlanır. Bu örnek nereden geldiğini dışarı aktarılan bölümün tarafından denetlenir *oluşturma ilkesi*.  
  
 İki olası oluşturma ilke *paylaşılan* ve *paylaşılmayan*. Paylaşılan bir oluşturma ilkesiyle parçası sözleşme ile bir bölümü için kapsayıcıdaki her bir içeri aktarma arasında paylaştırılır. Bileşim motoru eşleşme bulur ve içeri aktarılırken bir özelliği ayarlamak yalnızca biri zaten mevcut değilse yeni bir kopya bölümünün örneği oluşturulmaz; Aksi takdirde, mevcut kopyalama kullanacaksınız. Bu, çok sayıda nesne aynı bölüme başvuruları olabileceği anlamına gelir. Bu bölümleri, birçok yerde değiştirilebilir; iç durumu dayanarak doğrulamamalısınız. Bu ilke, statik bölümleri, hizmetleri sağlamak bölümleri ve çok fazla bellek veya diğer kaynakları tüketen bölümleri için uygundur.  
  
 Aktarımlarından biri için eşleşen bir içeri aktarma bulunan her zaman bir parçası oluşturma ilkesine paylaşılmayan oluşturulur. Parçanın dışarı aktarılan sözleşme biriyle eşleşen bir kapsayıcıdaki her bir içeri aktarma için yeni bir kopyasını dolayısıyla örneği oluşturulur. Bu kopyalar iç durumu paylaşılmaz. Bu ilke, burada kendi iç durumu her içeri aktarma gerektirir bölümleri için uygundur.  
  
 Hem içeri aktarma ve dışarı aktarma değerleri arasından bir bölümü oluşturma ilkesi belirleyebilirsiniz `Shared`, `NonShared`, veya `Any`. Varsayılan değer `Any` hem içeri ve dışarı aktarımların. Belirten bir dışarı aktarma `Shared` veya `NonShared` yalnızca aynı belirtir ya da belirten bir içeri aktarma eşleşecektir `Any`. Benzer şekilde, belirten alma `Shared` veya `NonShared` yalnızca aynı belirtir ya da belirten bir dışarı aktarma eşleşecektir `Any`. İçeri ve dışarı aktarmalar uyumsuz oluşturma ilkeleri ile bir eşleşme aynı şekilde bir içeri aktarma ve dışarı aktarma, sözleşme adı ya da sözleşme türü bir eşleşme değil olarak kabul edilmez. İçeri aktarma ve dışarı aktarma hem de belirtirseniz `Any`, değil oluşturma ilkesi belirtin veya varsayılan `Any`, paylaşılan oluşturma ilkesi varsayılan olur.  
  
 Aşağıdaki örnek, içeri aktarmalar hem oluşturma ilkeleri belirtme dışarı aktarmaları gösterir. `PartOne` Varsayılan olarak, bu nedenle, bir oluşturma ilkesi belirtmiyor `Any`. `PartTwo` Varsayılan olarak, bu nedenle, bir oluşturma ilkesi belirtmiyor `Any`. Her ikisi de içeri ve dışarı aktarmak için varsayılan olduğundan `Any`, `PartOne` paylaşılır. `PartThree` belirtir bir `Shared` oluşturma ilkesi, bu nedenle `PartTwo` ve `PartThree` aynı kopyasını paylaşır `PartOne`. `PartFour` belirtir bir `NonShared` oluşturma ilkesi, bu nedenle `PartFour` içinde paylaşılmayan olacaktır `PartFive`. `PartSix` belirtir bir `NonShared` oluşturma ilkesi. `PartFive` ve `PartSix` her ayrı kopyası alırsınız `PartFour`. `PartSeven` belirtir bir `Shared` oluşturma ilkesi. Olduğundan dışarı aktarılan `PartFour` oluşturma ilkesi ile `Shared`, `PartSeven` alma herhangi bir şey eşleşmiyor ve doldurulmaz.  
  
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
 Kapsayıcının içinde bölümleri barındırıldığından, yaşam döngüsü sıradan nesnelerden daha karmaşık olabilir. Bölümleri iki önemli yaşam döngüsü ile ilgili arabirimler uygulayabilirsiniz: `IDisposable` ve `IPartImportsSatisfiedNotification`.  
  
 Aşağı kapatma sırasında gerçekleştirilecek işin gerektiren veya kaynakları serbest bırakmak gereken bölümleri uygulamanız gerekir `IDisposable`, .NET Framework nesneleri için her zamanki gibi. Ancak, kapsayıcı oluşturur ve bölümleri başvuruları korur olduğundan, yalnızca bir bölüm kapsayıcı çağırmalıdır `Dispose` yöntemini. Kapsayıcı uygulayan `IDisposable`ve kendisinin temizleme bölümü olarak `Dispose` çağırır `Dispose` sahip olduğu tüm bölümleri. Ve sahip olduğu herhangi bir bölümü artık gerekli değilse bu nedenle, her zaman kapsayıcının silmesi gerekir.  
  
 Uzun süreli bileşim kapsayıcılar için bellek tüketimi paylaşılmayan oluşturma ilkesi ile parçaları tarafından bir sorun olabilir. Bu paylaşılmayan bölümler birden çok kez oluşturulabilir ve kapsayıcı atılana kadar elden değil. Bu işlemel için kapsayıcı sağlar. `ReleaseExport` yöntemi. Bu yöntemin çağrılması bir paylaşılmayan dışarı aktarma, dışarı aktarma kaldırır ve siler. Yalnızca vb. ağaç aşağı kaldırılan dışarı aktarma tarafından kullanılan bölümleri de kaldırılır ve atıldı. Bu şekilde, kaynakları bileşim kapsayıcı disposing olmadan kazanılabilir.  
  
 `IPartImportsSatisfiedNotification` adlı bir yöntem içerir `OnImportsSatisfied`. Bu yöntem, kapsayıcının oluşturma tamamlandı ve parça içeri aktarmalar kullanım için hazır olduğunuzda arabirimi uygulayan herhangi bir bölümü şirket tarafından çağrılır. Bölümleri aktarımlarının diğer bölümlerini doldurmak için bileşim motoru tarafından oluşturulur. Imports bölümünün ayarlamadan önce kullanır veya bu değerleri kullanarak önkoşul olarak belirtilmedi sürece bölümü oluşturucuda içeri aktarılan değerlerini işleyen başlatma gerçekleştirilemiyor `ImportingConstructor` özniteliği. Bu genellikle tercih edilen yöntemdir, ancak bazı durumlarda, oluşturucu ekleme kullanılamayabilir. Bu gibi durumlarda, başlatma gerçekleştirilebilir `OnImportsSatisfied`, ve bölümü uygulamalıdır `IPartImportsSatisfiedNotification`.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Kanal 9 Video: Yönetilen Genişletilebilirlik Çerçevesi ile uygulamalarınızı açın](https://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)
- [Kanal 9 Video: Yönetilen Genişletilebilirlik Çerçevesi (MEF) 2.0](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)
