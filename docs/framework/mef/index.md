---
title: Managed Extensibility Framework (MEF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f950779514975a3ee76af76506c7579e046537f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)
Bu konu, .NET Framework 4'te tanıtılan Yönetilen Genişletilebilirlik Çerçevesi genel bir bakış sağlar.  
  
<a name="what_is_mef"></a>   
## <a name="what-is-mef"></a>MEF nedir?  
 Genişletilebilirlik Çerçevesi ile yönetilen veya MEF hafif, Genişletilebilir uygulamaları oluşturmak için bir kitaplık değil. Uygulama geliştiricilerinin bulmak ve yapılandırma gerektirmeden uzantıları kullanmak sağlar. Ayrıca kolayca kod kapsüllemek ve kırılacak sabit bağımlılıkları kaçının Uzantı geliştiricilerine olanak tanır. MEF değil yalnızca uygulama içinden ancak de uygulamalar arasında yeniden kullanılabilir uzantıları sağlar.  
  
<a name="the_problem_of_extensibility"></a>   
## <a name="the-problem-of-extensibility"></a>Genişletilebilirlik sorunu  
 Genişletilebilirlik için destek sağlayan büyük bir uygulamanın Mimarı olduğunuzu varsayalım. Uygulamanız daha küçük bileşenlerden çok sayıda içermek zorundadır ve oluşturma ve bunları çalıştırmaya sorumludur.  
  
 En basit sorun için kaynak kodu, uygulamanızda bileşenleri içerir ve doğrudan kodunuzdan çağrı yaklaşımdır.  Bunun bir belirgin bazı dezavantajları vardır.  En önemlisi, örneğin, bir Web uygulamasında, kabul edilebilir, ancak bir istemci uygulamasında çalışmaz bir kısıtlama kaynak kodunu değiştirmeden yeni bileşenler ekleyemezsiniz.  Üçüncü tarafların ve bunları sizin erişmek izin veremez aynı nedenden dolayı geliştirilebilir için eşit oranda sorunlu olmasa da, bileşenler için kaynak koduna erişim olmayabilir.  
  
 Bir uzantı noktası veya uygulama ve bileşenlerinin bağlantıyı kesmeye izin vermek için arabirim sağlamak için biraz daha karmaşık bir yaklaşım olacaktır.  Bu model altında bir bileşen uygulayabileceğiniz bir arabirim ve uygulamanız ile etkileşim kurmak etkinleştirmek için bir API sağlayabilir.  Bu kaynak koduna erişim gerektiren sorununu çözer, ancak hala zorluklara sahiptir.  
  
 Uygulama bileşenleri kendi başına bulmak için tüm kapasite eksik olduğundan, hala açıkça hangi bileşenlerin mevcut olduğu ve yüklenmesi gerektiğini söylediyse gerekir.  Bu genellikle bir yapılandırma dosyasında kullanılabilir bileşenleri açıkça kaydederek gerçekleştirilir. Özellikle son kullanıcı ile güncelleştirme yapmak için beklenen geliştirici değil, ise bileşenleri sağlayan doğru Bunun anlamı bakım sorun haline gelir.  
  
 Ayrıca, birbirleriyle dışında uygulamanın kendisinin aracılığı tanımlanan kanallar iletişim kuramadığı bileşenleridir.  Uygulama Mimarı belirli bir iletişim için gereken beklenen değil, genellikle mümkün değildir.  
  
 Son olarak, bileşen geliştiricileri hangi derlemenin uyguladıkları arayüzü içeren üzerinde sıkı bir bağımlılık kabul etmeniz gerekir.  Bu durum, birden fazla uygulamada kullanılacak bir bileşen zorlaştırır ve bileşenleri için bir test çerçevesi oluşturduğunuzda sorunları da oluşturabilir.  
  
<a name="what_mef_provides"></a>   
## <a name="what-mef-provides"></a>MEF ne sağlar  
 Mevcut bileşenlerin açık kaydı yerine MEF dolaylı olarak bulmak için bir yol sağlar. aracılığıyla *birleşim*.  Adlı bir MEF Bileşeni, bir *bölümü*, bildirimli olarak hem bağımlılıklarını belirtir (olarak bilinen *alır*) ve hangi özelliklere (olarak bilinen *aktarır*) kullanılabilir hale getirir. Bir bölümü oluşturulduğunda, MEF bileşim motoru diğer bölümlerden kullanılabilir olan, içeri aktarmalar karşılar.  
  
 Bu yaklaşım önceki bölümde açıklanan sorunları çözer.  MEF bölümleri bildirimli olarak yeteneklerini belirtmek için çalışma zamanında keşfedilebilir oldukları sabit kodlanmış başvuruları veya kırılacak yapılandırma dosyalarını olmadan parçalar kullanımını uygulama yapabilir anlamına gelir.  MEF bulmak ve onları başlatmasını veya hatta kendi derlemeleri yükleme bölümleri bunların meta verilerini incelemek uygulamaları sağlar. Sonuç olarak, dikkatli bir şekilde nasıl ve ne zaman uzantıları yüklenmesi gerektiğini belirtmek için gerek yoktur.  
  
 Sağlanan dışarı aktarmaları ek olarak, bir bölümü diğer bölümler tarafından doldurulacak kendi içeri aktarmalar belirtebilirsiniz.  Bu yapar arasında iletişimi değil yalnızca olası ancak kolay bölümleri ve kodunu iyi bir şekilde düzenlenmesini sağlar. Örneğin, birçok bileşen için ortak hizmetler ayrı bir bölüm içinde ve kolayca değiştirilebilir veya değiştirildi.  
  
 MEF modeli belirli bir uygulama derlemesi üzerinde sıkı bir bağımlılık gerektirdiğinden, uygulamadan uygulamaya yeniden kullanılabilir uzantıları sağlar.  Bu ayrıca, uygulamayı uzantı bileşenlerini test etmek, bağımsız bir test bandı geliştirmek kolaylaştırır.  
  
 Uygulama Hizmetleri uzantılarını kullanıma sunmak için uzantı bileşenleri tarafından doldurulabilir ve da bildirebilir içe aktarır MEF kullanılarak yazılmış Genişletilebilir uygulama bildirir.  Her uzantı bileşeni verme bildirir ve içeri aktarımlar da bildirebilir.  Bu şekilde, uzantı bileşenlerinin kendileri otomatik olarak genişletilebilir.  
  
<a name="where_is_mef_available"></a>   
## <a name="where-is-mef-available"></a>Burada MEF var mı?  
 MEF bütünleyici bir [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]ve .NET Framework'ün yerde kullanıldığı kullanılabilir.  Windows Forms, WPF veya başka bir teknolojinin kullanıp veya ASP.NET kullanan sunucu uygulamaları, istemci uygulamalarınızda MEF kullanabilirsiniz.  
  
<a name="mef_and_maf"></a>   
## <a name="mef-and-maf"></a>MEF ve MAF  
 .NET Framework'ün önceki sürümlerini yönetilen eklenti Framework (yalıtmak ve uzantıları yönetmek uygulamalara izin vermek üzere tasarlanmış MAF) sunmuş.  MAF odak biraz daha yüksek düzeyli uzantı yalıtımına ve yüklenmesi ve kaldırılması MEF'in odak bulunabilirliği, genişletilebilirlik ve taşınabilirlik durumdayken derleme yoğunlaştırıcı MEF daha.  İki çerçeveleri düzgün çalışmasını ve tek bir uygulama hem de yararlanabilir.  
  
<a name="simplecalculator_an_example_application"></a>   
## <a name="simplecalculator-an-example-application"></a>SimpleCalculator: Örnek bir uygulama  
 En basit yolu MEF neler yapabileceğinizi görmek için basit bir MEF uygulaması oluşturmaktır. Bu örnekte, SimpleCalculator adlı çok basit bir hesap makinesi oluşturun. SimpleCalculator amacı "5 + 3" biçiminde temel aritmetik komutları kabul eden bir konsol uygulaması oluşturmaktır veya "6-2" ve doğru yanıt verir. MEF kullanarak uygulama kodunu değiştirmeden yeni işleçler eklemeniz mümkün olacaktır.  
  
 Bu örneğin tam kodu indirmek için bkz: [SimpleCalculator örnek](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).  
  
> [!NOTE]
>  SimpleCalculator amacı MEF sözdizimi ve kavramları göstermek için yerine mutlaka gerçekçi bir senaryo için kullanımı sağlamak için budur. MEF gücünü en yararlı uygulamaları çoğunu SimpleCalculator daha karmaşıktır. Daha kapsamlı örnekler için bkz: [Genişletilebilirlik Çerçevesi ile yönetilen](https://github.com/MicrosoftArchive/mef) github'da.
  
 , Başlatmak için [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], adlı yeni bir konsol uygulama projesi oluşturun `SimpleCalculator`. MEF bulunduğu System.ComponentModel.Composition derlemesine başvuru ekleyin. Module1.vb veya Program.cs açın ve eklemek `Imports` veya `using` System.ComponentModel.Composition ve System.ComponentModel.Composition.Hosting bildirimlerini. Bu iki ad alanı Genişletilebilir uygulama geliştirme için ihtiyaç duyduğunuz MEF türlerini içerir. Visual Basic'te eklemek `Public` anahtar sözcüğü bildirir satırına `Module1` modülü.  
  
<a name="composition_container_and_catalogs"></a>   
## <a name="composition-container-and-catalogs"></a>Kapsayıcının ve kataloglarını  
 MEF bileşim modelinin çekirdeği *kapsayıcının*, kullanılabilir tüm bölümleri içerir ve oluşturma işlemini gerçekleştirir.  (Diğer bir deyişle, içeri aktarmalar için aktarımlarla.)  Kapsayıcının en yaygın türü <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, ve bu SimpleCalculator için kullanır.  
  
 Visual Basic'te Module1.vb, adlı ortak bir sınıf ekleyin `Program`. Aşağıdaki satırı ekleyin `Program` Module1.vb veya Program.cs sınıfında:  
  
```vb  
Dim _container As CompositionContainer  
```  
  
```csharp  
private CompositionContainer _container;  
```  
  
 Bunun için birleşim kapsayıcıları kullanılabilir bölümleri bulmak için kullanır bir *katalog*. Bir katalog bazı kaynaklardaki bölümleri kullanılabilir hale getiren bir nesnedir.  MEF sağlanan türü, bir derlemeyi ya da dizin bölümlerini keşfetmenizi sağlar. Uygulama geliştiricilerinin Web hizmeti gibi diğer kaynaklardan kısımlarını keşfetmek için yeni katalog kolayca oluşturabilirsiniz.  
  
 Aşağıdaki oluşturucuyu ekleyin `Program` sınıfı:  
  
```vb  
Public Sub New()  
    'An aggregate catalog that combines multiple catalogs  
     Dim catalog = New AggregateCatalog()  
  
    'Adds all the parts found in the same assembly as the Program class  
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))  
  
    'Create the CompositionContainer with the parts in the catalog  
    _container = New CompositionContainer(catalog)  
  
    'Fill the imports of this object  
    Try  
        _container.ComposeParts(Me)  
    Catch ex As Exception  
        Console.WriteLine(ex.ToString)  
    End Try  
End Sub  
```  
  
```csharp  
private Program()  
{  
    //An aggregate catalog that combines multiple catalogs  
    var catalog = new AggregateCatalog();  
    //Adds all the parts found in the same assembly as the Program class  
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));  
  
    //Create the CompositionContainer with the parts in the catalog  
    _container = new CompositionContainer(catalog);  
  
    //Fill the imports of this object  
    try  
    {  
        this._container.ComposeParts(this);  
    }  
    catch (CompositionException compositionException)  
    {  
        Console.WriteLine(compositionException.ToString());  
   }  
}  
```  
  
 Çağrı <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> geçerli örneği bu durumda bölümleri belirli bir kümesini oluşturmak için kapsayıcının söyler `Program`. Bu noktada, ancak hiçbir şey, beri olacağını `Program` doldurmak için aktarımlara sahip değildir.  
  
<a name="imports_and_exports_with_attributes"></a>   
## <a name="imports-and-exports-with-attributes"></a>İçeri ve dışarı aktarmalar özniteliklere sahip  
 İlk olarak `Program` bir hesap makinesini içeri aktarır. Bu kullanıcı ayrılması, konsol giriş ve çıkış gireceğini gibi arabirimi sorunlarını sağlar `Program`, hesap makinesi mantığından.  
  
 Aşağıdaki kodu ekleyin `Program` sınıfı:  
  
```vb  
<Import(GetType(ICalculator))>  
Public Property calculator As ICalculator  
```  
  
```csharp  
[Import(typeof(ICalculator))]  
public ICalculator calculator;  
```  
  
 Dikkat bildirimi `calculator` nesne olağan dışı bir durum değil ancak ile donatılmış <xref:System.ComponentModel.Composition.ImportAttribute> özniteliği.  Bu öznitelik bir alma olması için bir şeyler bildirir; diğer bir deyişle, nesne oluşturulduğunda bileşim motoru tarafından doldurulur.  
  
 Her içeri aktarma sahip bir *sözleşme*, onu eşleşebilecek ile hangi dışarı belirler. Anlaşma açıkça belirtilmiş bir dize olabilir veya bu durumda arabirimi verilen bir türden MEF tarafından otomatik olarak da oluşturulabilir `ICalculator`.  Eşleşen bir anlaşma ile bildirilen tüm dışarı bu alma karşılar.  Türü unutmayın `calculator` nesnesidir aslında `ICalculator`, bu gerekli değildir. Sözleşme alma nesne türünden bağımsızdır.  (Bu durumda, dışlamayı `typeof(ICalculator)`.  MEF otomatik olarak açıkça belirtmediğiniz sürece alma türüne göre için sözleşme varsayar.)  
  
 Bu çok basit arabirim modüle ekleyin veya `SimpleCalculator` ad alanı:  
  
```vb  
Public Interface ICalculator  
    Function Calculate(ByVal input As String) As String  
End Interface  
```  
  
```csharp  
public interface ICalculator  
{  
    String Calculate(String input);  
}  
```  
  
 Tanımladığınız göre `ICalculator`, bunu uygulayan bir sınıf gerekir.  Aşağıdaki sınıf modülüne ekleyin veya `SimpleCalculator` ad alanı:  
  
```vb  
<Export(GetType(ICalculator))>  
Public Class MySimpleCalculator  
   Implements ICalculator  
  
End Class  
```  
  
```csharp  
[Export(typeof(ICalculator))]  
class MySimpleCalculator : ICalculator  
{  
  
}  
```  
  
 İçeri aktarma ile eşleşir verme işte `Program`. Alma eşleşecek şekilde dışa aktarmak için dışa aktarma aynı sözleşme olması gerekir.  Bir anlaşma altında dışarı aktarım temel alarak `typeof(MySimpleCalculator)` bir uyuşmazlık oluşturur ve içeri aktarma doldurulmadı; sözleşme tam olarak eşleşmesi gerekiyor.  
  
 Bu derlemede kullanılabilir tüm bölümleri içeren kapsayıcının doldurulur beri `MySimpleCalculator` bölümü kullanılabilir olacak.  Zaman Oluşturucusu `Program` üzerinde bileşim gerçekleştirdiğinde `Program` nesne, kendi alma ile doldurulur bir `MySimpleCalculator` bu amaç için oluşturulacak nesne.  
  
 Kullanıcı arabirim katmanı (`Program`) başka bir şey bilmek gerekmez.  Bu nedenle kullanıcı arabirimi mantığı geri kalanında doldurabilirsiniz `Main` yöntemi.  
  
 Aşağıdaki kodu ekleyin `Main` yöntemi:  
  
```vb  
Sub Main()  
    Dim p As New Program()  
    Dim s As String  
    Console.WriteLine("Enter Command:")  
    While (True)  
        s = Console.ReadLine()  
        Console.WriteLine(p.calculator.Calculate(s))  
    End While  
End Sub  
```  
  
```csharp  
static void Main(string[] args)  
{  
    Program p = new Program(); //Composition is performed in the constructor  
    String s;  
    Console.WriteLine("Enter Command:");  
    while (true)  
    {  
        s = Console.ReadLine();  
        Console.WriteLine(p.calculator.Calculate(s));  
    }  
}  
```  
  
 Bu kod yalnızca bir satır girişi ve çağrıları okur `Calculate` işlevinin `ICalculator` geri konsola yazar sonucu üzerinde. İçinde ihtiyacınız olan tüm kod `Program`.  İş tüm kalan bölümlerinde gerçekleşir.  
  
<a name="further_imports_and_importmany"></a>   
## <a name="further-imports-and-importmany"></a>Daha fazla içeri aktarma ve ImportMany  
 Genişletilebilir olmak üzere SimpleCalculator sırayla işlemlerinin bir listesini almak gerekir. Sıradan <xref:System.ComponentModel.Composition.ImportAttribute> özniteliği bir ve yalnızca bir tarafından doldurulur <xref:System.ComponentModel.Composition.ExportAttribute>.  Birden fazla olup olmadığını bileşim motoru hata verir.  Herhangi bir sayıda dışarı doldurulabilir bir alma oluşturmak için kullanabileceğiniz <xref:System.ComponentModel.Composition.ImportManyAttribute> özniteliği.  
  
 Aşağıdaki işlemleri özelliği Ekle `MySimpleCalculator` sınıfı:  
  
```vb  
<ImportMany()>  
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))  
```  
  
```csharp  
[ImportMany]  
IEnumerable<Lazy<IOperation, IOperationData>> operations;  
```  
  
 <xref:System.Lazy%602> bir tür dışarı başvuruları dolaylı olarak tutmak için MEF tarafından sağlanır.  Burada, dışarı aktarılan nesnenin kendisinin yanı sıra, aynı zamanda alırsınız *meta verileri dışarı aktarma*, ya da dışarı aktarılan nesnenin açıklayan bilgiler. Her <xref:System.Lazy%602> içeren bir `IOperation` gerçek bir işlemi temsil eden nesne ve bir `IOperationData` meta verilerini temsil eden nesne.  
  
 Aşağıdaki basit modülü arabirimler veya `SimpleCalculator` ad alanı:  
  
```vb  
Public Interface IOperation  
    Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer  
End Interface  
  
Public Interface IOperationData  
    ReadOnly Property Symbol As Char  
End Interface  
```  
  
```csharp  
public interface IOperation  
{  
     int Operate(int left, int right);  
}  
  
public interface IOperationData  
{  
    Char Symbol { get; }  
}  
```  
  
 Bu durumda, her işlem için meta veriler olduğunu gibi bu işlemi temsil eden simgeyi +, -, * ve benzeri. Ek işlemi kullanılabilir yapmak için aşağıdaki sınıfı modüle ekleyin veya `SimpleCalculator` ad alanı:  
  
```vb  
<Export(GetType(IOperation))>  
<ExportMetadata("Symbol", "+"c)>  
Public Class Add  
    Implements IOperation  
  
    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate  
        Return left + right  
    End Function  
End Class  
```  
  
```csharp  
[Export(typeof(IOperation))]  
[ExportMetadata("Symbol", '+')]  
class Add: IOperation  
{  
    public int Operate(int left, int right)  
    {  
        return left + right;  
    }  
}  
```  
  
 <xref:System.ComponentModel.Composition.ExportAttribute> Önce yaptığınız gibi işlevler özniteliği.  <xref:System.ComponentModel.Composition.ExportMetadataAttribute> Özniteliği bu dışarı meta verileri, formun ad-değer çifti ekler.  Sırada `Add` uygulayan sınıf `IOperation`, uygulayan bir sınıf `IOperationData` açıkça tanımlı değil. Bunun yerine, bir sınıf sağlanan meta verilerin adlarına göre özellikleriyle örtük olarak MEF tarafından oluşturulur.  (MEF meta verilerine erişmek için çeşitli yollardan budur.)  
  
 MEF bileşimiyse *özyinelemeli*. Açık olarak oluşturdunuz `Program` içeri aktarılan nesne bir `ICalculator` , türü dönüştü `MySimpleCalculator`.  `MySimpleCalculator`, sırasıyla bir koleksiyonunu alır `IOperation` nesneleri ve Al ne zaman doldurulur `MySimpleCalculator` aktarımlarının aynı zamanda oluşturulan `Program`. Varsa `Add` sınıf bildirilen çok doldurulması ve böyle devam etmesi gereken başka bir alma. Herhangi bir birleşim hatası sol doldurulmamış sonuçları alın.  (Ancak, içeri aktarmalar isteğe bağlı veya varsayılan değerleri atamak için bildirmek için mümkündür.)  
  
<a name="calculator_logic"></a>   
## <a name="calculator-logic"></a>Hesaplayıcı mantığı  
 Bu bölümleri yerinde, kalan tek şey hesaplayıcı mantığı. Aşağıdaki kodu ekleyin `MySimpleCalculator` uygulamak için sınıf `Calculate` yöntemi:  
  
```vb  
Public Function Calculate(ByVal input As String) As String Implements ICalculator.Calculate  
    Dim left, right As Integer  
    Dim operation As Char  
    Dim fn = FindFirstNonDigit(input) 'Finds the operator  
    If fn < 0 Then  
        Return "Could not parse command."  
    End If  
    operation = input(fn)  
    Try  
        left = Integer.Parse(input.Substring(0, fn))  
        right = Integer.Parse(input.Substring(fn + 1))  
    Catch ex As Exception  
        Return "Could not parse command."  
    End Try  
    For Each i As Lazy(Of IOperation, IOperationData) In operations  
        If i.Metadata.symbol = operation Then  
            Return i.Value.Operate(left, right).ToString()  
        End If  
    Next  
    Return "Operation not found!"  
End Function  
```  
  
```csharp  
public String Calculate(String input)  
{  
    int left;  
    int right;  
    Char operation;  
    int fn = FindFirstNonDigit(input); //finds the operator  
    if (fn < 0) return "Could not parse command.";  
  
    try  
    {  
        //separate out the operands  
        left = int.Parse(input.Substring(0, fn));  
        right = int.Parse(input.Substring(fn + 1));  
    }  
    catch   
    {  
        return "Could not parse command.";  
    }  
  
    operation = input[fn];  
  
    foreach (Lazy<IOperation, IOperationData> i in operations)  
    {  
        if (i.Metadata.Symbol.Equals(operation)) return i.Value.Operate(left, right).ToString();  
    }  
    return "Operation Not Found!";  
}  
```  
  
 Sol ve sağ işlenen giriş dizeye ve bir işleç karakter başlangıç adımları ayrıştırır.  İçinde `foreach` döngü, her üyesi `operations` koleksiyonu incelenir. Bu nesnelerin türündedir <xref:System.Lazy%602>, ve meta veri değerleri ve dışarı aktarılan nesne ile erişilebilir <xref:System.Lazy%602.Metadata%2A> özelliği ve <xref:System.Lazy%601.Value%2A> özelliği sırasıyla. Bu durumda, `Symbol` özelliği `IOperationData` nesne bulunan hesaplayıcı çağrıları bir eşleşme olarak `Operate` yöntemi `IOperation` nesne ve sonucu döndürür.  
  
 Hesaplayıcı tamamlamak için ayrıca ilk karakterin rakam olmayan bir dize döndürür yardımcı yöntemi gerekir.  Aşağıdaki yardımcı yöntemi ekleyin `MySimpleCalculator` sınıfı:  
  
```vb  
Private Function FindFirstNonDigit(ByVal s As String) As Integer  
    For i = 0 To s.Length  
        If (Not (Char.IsDigit(s(i)))) Then Return i  
    Next  
    Return -1  
End Function  
```  
  
```csharp  
private int FindFirstNonDigit(String s)  
{  
    for (int i = 0; i < s.Length; i++)  
    {  
        if (!(Char.IsDigit(s[i]))) return i;  
    }  
    return -1;  
}  
```  
  
 Artık derlemek ve projeyi çalıştırmak mümkün olması gerekir. Visual Basic'te, eklediğiniz emin olun `Public` anahtar `Module1`. Konsol penceresinde "5 + 3" gibi bir toplama işlemi yazın ve hesaplayıcı sonuçları döndürür.  Herhangi bir işleç "işlemi bulunamadı!" neden olur İleti.  
  
<a name="extending_simplecalculator_using_a_new_class"></a>   
## <a name="extending-simplecalculator-using-a-new-class"></a>Yeni bir sınıf kullanarak SimpleCalculator'ı genişletme  
 Hesaplayıcı çalışır, yeni bir işlem eklemek kolaydır. Aşağıdaki sınıf modülüne ekleyin veya `SimpleCalculator` ad alanı:  
  
```vb  
<Export(GetType(IOperation))>  
<ExportMetadata("Symbol", "-"c)>  
Public Class Subtract  
    Implements IOperation  
  
    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate  
        Return left - right  
    End Function  
End Class  
```  
  
```csharp  
[Export(typeof(IOperation))]  
[ExportMetadata("Symbol", '-')]  
class Subtract : IOperation  
{  
    public int Operate(int left, int right)  
    {  
        return left - right;  
    }  
}  
```  
  
 Derleme ve projeyi çalıştırın. "5-3" gibi bir çıkarma işlemi yazın. Hesaplayıcı artık çıkarma yanı sıra eklenmesini destekler.  
  
<a name="extending_simplecalculator_using_a_new_assembly"></a>   
## <a name="extending-simplecalculator-using-a-new-assembly"></a>Yeni bir derleme kullanarak SimpleCalculator'ı genişletme  
 Sınıf ekleme kaynak kod yetecek kadar basittir ancak MEF bölümleri için dışında bir uygulamanın kendi kaynak konum olanağı sağlar. Bunu göstermek için SimpleCalculator ekleyerek bölümleri, kendi derlemesiyle yanı sıra, bir dizin aramak için değiştirmeniz gerekecektir bir <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.  
  
 Adlı yeni bir dizin ekleme `Extensions` SimpleCalculator projesine.  Proje düzeyinde ve çözüm düzeyinde eklediğinizden emin olun. Ardından yeni bir sınıf kitaplığı proje adlı çözüme ekleyin `ExtendedOperations`. Yeni proje ayrı bir derleme derlenir.  
  
 ExtendedOperations projesi için proje özelliklerini Tasarımcısı'nı açın ve'ı tıklatın **derleme** veya **yapı** sekmesi. Değişiklik **yapı çıkış yolu** veya **çıkış yolu** SimpleCalculator proje dizininde uzantıları dizinine işaret edecek şekilde (.. \SimpleCalculator\Extensions\\).  
  
 Module1.vb veya Program.cs içinde aşağıdaki satırı ekleyin `Program` Oluşturucusu:  
  
```vb  
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))  
```  
  
```csharp  
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));  
```  
  
 Örnek yolu Extensions dizini yolu değiştirin.  (Bu mutlak hata ayıklama amacıyla yalnızca yoludur.  Bir üretim uygulamasında, göreli bir yol kullanırsınız.) <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> Kapsayıcının uzantıları dizindeki tüm derlemelerde bulunan tüm bölümler şimdi ekleyeceksiniz.  
  
 ExtendedOperations projede başvuruları SimpleCalculator ve System.ComponentModel.Composition ekleyin. ExtendedOperations sınıf dosyası ekleyin bir `Imports` veya `using` System.ComponentModel.Composition bildirimi. Visual Basic'te de eklemeniz bir `Imports` SimpleCalculator deyimi. Daha sonra aşağıdaki sınıf ExtendedOperations sınıfı dosyaya ekleyin:  
  
```vb  
<Export(GetType(SimpleCalculator.IOperation))>  
<ExportMetadata("Symbol", "%"c)>  
Public Class Modulo  
    Implements IOperation  
  
    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate  
        Return left Mod right  
    End Function  
End Class  
```  
  
```csharp  
[Export(typeof(SimpleCalculator.IOperation))]  
[ExportMetadata("Symbol", '%')]  
public class Mod : SimpleCalculator.IOperation  
{  
    public int Operate(int left, int right)  
    {  
        return left % right;  
    }  
}  
```  
  
 Bu da sipariş eşleşecek şekilde sözleşme için Not <xref:System.ComponentModel.Composition.ExportAttribute> özniteliği, aynı türde olmalıdır <xref:System.ComponentModel.Composition.ImportAttribute>.  
  
 Derleme ve projeyi çalıştırın. Yeni Mod (%) işleci sınayın.  
  
<a name="conclusion"></a>   
## <a name="conclusion"></a>Sonuç  
 Bu konuda MEF temel kavramlarını ele.  
  
-   Parça, kataloglar ve kapsayıcının  
  
     Bölümleri ve kapsayıcının bir MEF uygulamasının temel yapı taşlarının var. Alır ya da yukarı kendisi de dahil bir değer verir herhangi bir nesne bir parçasıdır. Bir katalog belirli bir kaynaktan kısımlarının bir koleksiyonunu sağlar.  Kapsayıcının birleşim, içeri aktarmalar dışarı bağlama gerçekleştirmek için bir katalog tarafından sağlanan bölümleri kullanır.  
  
-   İçeri ve dışarı aktarmalar  
  
     İçeri ve dışarı aktarmalar olarak bileşenleri iletişim yoludur. Bir alma ile belirli bir değer veya nesne gereksinimini bileşeni belirtir ve isteğe bağlı olarak verme ile bir değer kullanılabilirliğini belirtir. Her içeri aktarma, dışarı sözleşmesi yapmamanız listesiyle eşleştirilir.  
  
<a name="where_do_i_go_now"></a>   
## <a name="where-do-i-go-now"></a>I şimdi nereye?  
 Bu örneğin tam kodu indirmek için bkz: [SimpleCalculator örnek](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).  
  
 Daha fazla bilgi ve kod örnekleri için bkz: [Genişletilebilirlik Çerçevesi ile yönetilen](http://go.microsoft.com/fwlink/?LinkId=144282). MEF türlerinin listesi için bkz: <xref:System.ComponentModel.Composition?displayProperty=nameWithType> ad alanı.
