---
title: Nesne odaklı programlama (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 0dee6edf966e8e2a3e430e60f1c3d51354d08bf3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="object-oriented-programming-c"></a>Nesne odaklı programlama (C#)
C# kapsülleme, devralma ve çok biçimlilik dahil nesne odaklı programlama için tam destek sağlar.  
  
 *Kapsülleme* ilgili özellikleri, yöntemleri ve diğer üyeleri bir grup kabul edilir olduğunu tek bir birim veya nesne olarak anlamına gelir.  
  
 *Devralma* var olan bir sınıfına dayalı yeni sınıflar oluşturma olanağı açıklar.  
  
 *Çok biçimlilik* farklı yollarla aynı özelliklerinin veya yöntemlerin her sınıf uygulayan olsa bile, birbirinin yerine, kullanılabilir birden çok sınıf olabilir anlamına gelir.  
  
 Bu bölümde aşağıdaki kavramlar açıklanmaktadır:  
  
-   [Sınıflar ve nesneler](#Classes)  
  
    -   [Sınıf üyeleri](#Members)  
  
         [Özellikleri ve alanları](#Properties)  
  
         [Yöntemler](#Methods)  
  
         [Oluşturucular](#Constructors)  
  
         [Sonlandırıcılar](#Finalizers)  
  
         [Olaylar](#Events)  
  
         [İç içe geçmiş sınıflar](#NestedClasses)  
  
    -   [Erişim değiştiricileri ve erişim düzeyleri](#AccessModifiers)  
  
    -   [Örnek oluşturma sınıfları](#InstantiatingClasses)  
  
    -   [Statik sınıflar ve üyeleri](#Static)  
  
    -   [Anonim Tipler](#AnonymousTypes)  
  
-   [Devralma](#Inheritance)  
  
    -   [Üyeleri geçersiz kılma](#Overriding)  
  
-   [Arabirimler](#Interfaces)  
  
-   [Genel Türler](#Generics)  
  
-   [Temsilciler](#Delegates)  
  
##  <a name="Classes"></a> Sınıflar ve nesneler  
 Koşulları *sınıfı* ve *nesne* bazen birbirinin yerine, ancak aslında, sınıfları açıklar kullanılan *türü* nesnelerin nesneleri kullanılabilir durumdayken  *örnekleri* sınıfların. Bu nedenle, bir nesne oluşturma işlemi adlı *örneklemesi*. Şeması benzerleme kullanarak şeması sınıftır ve o şeması yapılan bir yapı bir nesnedir.  
  
 Bir sınıf tanımlamak için:  
  
```csharp  
class SampleClass  
{  
}  
```  
  
 C# ayrıca sağlar adlı sınıflar açık bir sürümünü *yapıları* büyük nesneler dizisi oluşturmak ve gerektiğinde faydalı olan çok fazla bellek için kullanmak istediğiniz değil.  
  
 Bir yapı tanımlamak için:  
  
```csharp  
struct SampleStruct  
{  
}  
```  
  
 Daha fazla bilgi için bkz.:  
  
-   [class](../../../csharp/language-reference/keywords/class.md)  
  
-   [struct](../../../csharp/language-reference/keywords/struct.md)  
  
###  <a name="Members"></a> Sınıf üyeleri  
 Her sınıf farklı olabilir *sınıfı üyeleri* sınıfı verileri, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasındaki iletişimi sağlamak olayları tanımlayan özelliği içerir.  
  
####  <a name="Properties"></a> Özellikleri ve alanları  
 Alanları ve özellikleri bir nesne içeren bilgileri temsil eder. Bunlar okunabilir veya doğrudan ayarlamak için alanları gibi değişkenlerdir.  
  
 Bir alan tanımlamak için:  
  
```csharp  
class SampleClass  
{  
    public string sampleField;  
}  
```  
  
 Özelliklerin get ve değerleri nasıl ayarlayın veya döndürülen üzerinde daha fazla denetim sağlamak yordamları ayarlayın.  
  
 C#, özellik değeri depolamak için özel bir alan oluşturun veya bu alan otomatik olarak arka planda oluşturun ve özellik yordamlar için temel mantığın sözde ve otomatik uygulanan özellikler kullanmak üzere sağlar.  
  
 Otomatik uygulanan bir özellik tanımlamak için:  
  
```csharp  
class SampleClass  
{  
    public int SampleProperty { get; set; }  
}  
```  
  
 Özellik değeri depolamak için bir alan tanımlayın ve depolamak ve bunu alma için temel mantığı sağlar özellik değeri yazılırken okuma için bazı ek işlemler gerçekleştirmek ve gerekirse:  
  
```csharp  
class SampleClass  
{  
    private int _sample;  
    public int Sample  
    {  
        // Return the value stored in a field.  
        get { return _sample; }  
        // Store the value in the field.  
        set { _sample = value; }  
    }  
}  
```  
  
 Çoğu özellikleri yöntemleri ya da hem ayarlamak ve özellik değerini almak için yordamlar vardır. Ancak, okuma veya değiştirilmesini kısıtlamak için salt okunur veya salt yazılır özellikler oluşturabilirsiniz. C# ' ta, atlayabilirsiniz `get` veya `set` özelliği yöntemi. Ancak, otomatik uygulanan özellikler salt okunur veya sadece yazılabilir olamaz.  
  
 Daha fazla bilgi için bkz.:  
  
-   [get](../../../csharp/language-reference/keywords/get.md)  
  
-   [set](../../../csharp/language-reference/keywords/set.md)  
  
####  <a name="Methods"></a> Yöntemleri  
 A *yöntemi* bir nesne gerçekleştirebileceğiniz bir eylemdir.  
  
 Bir sınıfın bir yöntemi tanımlamak için:  
  
```csharp  
class SampleClass  
{  
    public int sampleMethod(string sampleParam)  
    {  
        // Insert code here  
    }  
}  
```  
  
 Bir sınıf çeşitli uygulamalarını olabilir veya *aşırı*, aynı yönteminin parametreleri veya parametre türleri sayısında farklılık gösterir.  
  
 Bir yöntem aşırı yükleme için:  
  
```csharp  
public int sampleMethod(string sampleParam) {};  
public int sampleMethod(int sampleParam) {}  
```  
  
 Çoğu durumda bir sınıf tanımı içinde bir yöntem bildirin. Ancak, ayrıca C# destekler *genişletme yöntemleri* sınıfının gerçek tanımının dışında varolan bir sınıfı yöntemleri eklemek izin verir.  
  
 Daha fazla bilgi için bkz.:  
  
-   [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Genişletme Yöntemleri](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
  
####  <a name="Constructors"></a> Oluşturucular  
 Oluşturucular belirli bir türde bir nesne oluşturulduğunda, otomatik olarak yürütülen sınıfı yöntemleridir. Oluşturucular genellikle yeni nesnenin veri üyeleri başlatır. Yalnızca bir sınıf oluşturulduğunda sonra bir oluşturucu çalıştırabilirsiniz. Ayrıca, Oluşturucusu kodda, başka bir kod sınıfında önce her zaman çalışır. Ancak, başka bir yöntem için olduğu gibi aynı şekilde, birden çok Oluşturucusu aşırı oluşturabilirsiniz.  
  
 Bir sınıf için bir oluşturucu tanımlamak için:  
  
```csharp  
public class SampleClass  
{  
    public SampleClass()  
    {  
        // Add code here  
    }  
}  
```  
  
 Daha fazla bilgi için bkz.:  
  
 [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md).  
  
####  <a name="Finalizers"></a> Sonlandırıcılar  
 Sonlandırıcılar sınıfların örneklerini destruct için kullanılır. .NET Framework Atık toplayıcısının ayırma ve uygulamanızda yönetilen nesneler için bellek sürümü otomatik olarak yönetir. Ancak, uygulamanızın oluşturduğu herhangi yönetilmeyen kaynakları temizlemek için sonlandırıcılar hala gerekebilir. Yalnızca bir olabilir sonlandırıcılar bir sınıf için.  
  
 Sonlandırıcılar ve .NET Framework atık toplama hakkında daha fazla bilgi için bkz: [çöp toplama](../../../standard/garbage-collection/index.md).  
  
####  <a name="Events"></a> Olayları  
 Bir sınıf olayları etkinleştirin veya diğer sınıflar bildirmek için nesne veya nesnelerin çeken bir şey olduğunda oluşur. Olay gönderir (veya oluşturur) sınıf adlı *yayımcı* ve olay alın (veya ele) sınıfları adlı *aboneleri*. Olaylar hakkında daha fazla bilgi için nasıl oluşturulur ve işlenmiş, bkz: [olayları](../../../standard/events/index.md).  
  
-   Bir sınıftaki bir olay bildirmek için kullanın [olay](../../../csharp/language-reference/keywords/event.md) anahtar sözcüğü.  
  
-   Bir olay yükseltmek için olay temsilcisini çağırır.  
  
-   Bir olaya abone olmak için kullanmak `+=` bir olayından aboneliği kullanmak için işleci; `-=` işleci.  
  
####  <a name="NestedClasses"></a> İç içe geçmiş sınıflar  
 Başka bir sınıfın içinde tanımlanmış bir sınıf olarak adlandırılan *iç içe geçmiş*. Varsayılan olarak, iç içe geçmiş sınıf özeldir.  
  
```csharp  
class Container  
{  
    class Nested  
    {  
        // Add code here.  
    }  
}  
```  
  
 İç içe geçmiş sınıf örneği oluşturmak için nokta tarafından takip ve iç içe geçmiş sınıf adına göre ve ardından kapsayıcı sınıfın adını kullanın:  
  
```csharp  
Container.Nested nestedInstance = new Container.Nested()  
```  
  
###  <a name="AccessModifiers"></a> Erişim değiştiricileri ve erişim düzeyleri  
 Tüm sınıflar ve sınıf üyeleri sağladıkları diğer sınıflara kullanarak hangi erişim düzeyi belirtebilirsiniz *erişim değiştiricileri*.  
  
 Aşağıdaki erişim değiştiricileri kullanılabilir:  
  
|C# değiştiricisi|Tanım|  
|------------------|----------------|  
|[public](../../../csharp/language-reference/keywords/public.md)|Tür veya üye, başka bir kod aynı bütünleştirilmiş kodda ya da başvurduğu başka bir derleme tarafından erişilebilir.|  
|[private](../../../csharp/language-reference/keywords/private.md)|Tür veya üye yalnızca aynı sınıfta kodu tarafından erişilebilir.|  
|[protected](../../../csharp/language-reference/keywords/protected.md)|Tür veya üye yalnızca kodu aynı sınıfın veya türetilmiş bir sınıf tarafından erişilebilir.|  
|[internal](../../../csharp/language-reference/keywords/internal.md)|Tür veya üye, herhangi bir kod aynı bütünleştirilmiş kodda değiştirebilir, ancak başka bir derleme tarafından erişilebilir.|  
|[protected internal](../../../csharp/language-reference/keywords/protected-internal.md)|Tür veya üye aynı bütünleştirilmiş kod veya başka bir derlemede herhangi bir türetilmiş sınıf tarafından erişilebilir.|  
|[private protected](../../../csharp/language-reference/keywords/private-protected.md)|Tür veya üye kodu aynı sınıfın veya temel sınıf derlemedeki türetilmiş bir sınıf tarafından erişilebilir.|  
  
 Daha fazla bilgi için bkz: [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
###  <a name="InstantiatingClasses"></a> Örnek oluşturma sınıfları  
 Nesne oluşturmak için bir sınıf örneği veya bir sınıf örneği oluşturmak gerekir.  
  
```csharp  
SampleClass sampleObject = new SampleClass();  
```  
  
 Bir sınıf örneği sonra değerleri örneğin özellikleri ve alanları atayın ve sınıf yöntemlerini çağırın.  
  
```csharp  
// Set a property value.  
sampleObject.sampleProperty = "Sample String";  
// Call a method.  
sampleObject.sampleMethod();  
```  
  
 Sınıf örnek oluşturma işlemi sırasında özellikleri değerleri atamak için nesne başlatıcıları kullanın:  
  
```csharp  
// Set a property value.  
SampleClass sampleObject = new SampleClass   
    { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 Daha fazla bilgi için bkz.:  
  
-   [new İşleci](../../../csharp/language-reference/keywords/new-operator.md)  
  
-   [Nesne ve Koleksiyon Başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
  
###  <a name="Static"></a> Statik sınıflar ve üyeleri  
 Bir statik sınıf özelliği, yordam veya bir sınıfın tüm örnekleri tarafından paylaşılan alan üyesidir.  
  
 Statik bir üyenin tanımlamak için:  
  
```csharp  
static class SampleClass  
{  
    public static string SampleString = "Sample String";  
}  
```  
  
 Statik üye erişmek için bu sınıfın bir nesnesi oluşturmadan sınıfın adını kullanın:  
  
```csharp  
Console.WriteLine(SampleClass.SampleString);  
```  
  
 C# statik sınıflar yalnızca statik üyeleri sahip ve örneği oluşturulamıyor. Statik üyeler statik olmayan özellikler, alanlar veya yöntemler de erişemiyor  
  
 Daha fazla bilgi için bkz: [statik](../../../csharp/language-reference/keywords/static.md).  
  
###  <a name="AnonymousTypes"></a> Anonim türler  
 Anonim türler veri türü için bir sınıf tanımı yazmadan nesneleri oluşturmak etkinleştirin. Bunun yerine, derleyici bir sınıf sizin için oluşturur. Sınıf kullanılabilir adı yok ve nesne bildirme belirttiğiniz özellikler içerir.  
  
 Anonim bir türün bir örneğini oluşturmak için:  
  
```csharp  
// sampleObject is an instance of a simple anonymous type.  
var sampleObject =   
    new { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 Daha fazla bilgi için bkz: [anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
##  <a name="Inheritance"></a> Devralma  
 Devralma yeniden kullanır, genişletir ve başka bir sınıf içinde tanımlanan davranışını değiştiren yeni bir sınıf oluşturmanıza olanak sağlar. Üyeleri devralındığı sınıfı adlı *temel sınıfı*, bu üyeler devralan sınıf adı verilen ve *türetilmiş sınıf*. Ancak, C# tüm sınıflar örtük olarak devralınmalıdır <xref:System.Object> .NET sınıf hiyerarşisi destekleyen ve tüm sınıfları için alt düzey hizmetleri sağlayan sınıf.  
  
> [!NOTE]
>  C# birden çok devralma desteklemiyor. Diğer bir deyişle, türetilmiş bir sınıf için yalnızca bir temel sınıf belirtebilirsiniz.  
  
 Bir taban sınıftan devralın için:  
  
```csharp  
class DerivedClass:BaseClass{}  
```  
  
 Varsayılan olarak tüm sınıflar devralınabilir. Ancak, bir sınıfın temel sınıf olarak kullanılmamalıdır veya yalnızca bir temel sınıf olarak kullanılan bir sınıf oluşturun olup olmadığını belirtebilirsiniz.  
  
 Bir sınıfın temel sınıf olarak kullanılan belirtmek için:  
  
```csharp  
public sealed class A { }  
```  
  
 Sınıfı yalnızca bir temel sınıf olarak kullanılabilir ve başlatılamaz belirtmek için:  
  
```csharp  
public abstract class B { }  
```  
  
 Daha fazla bilgi için bkz.:  
  
-   [sealed](../../../csharp/language-reference/keywords/sealed.md)  
  
-   [abstract](../../../csharp/language-reference/keywords/abstract.md)  
  
###  <a name="Overriding"></a> Üyeleri geçersiz kılma  
 Varsayılan olarak, türetilmiş bir sınıf tüm üyelerin kendi taban sınıfından devralıyor. Devralınan üye davranışını değiştirmek istiyorsanız, bunu geçersiz kılmanız gerekir. Diğer bir deyişle, yeni bir uygulama yöntemi, özelliği veya olay türetilen sınıfta tanımlayabilirsiniz.  
  
 Aşağıdaki değiştiricileri özellikleri ve yöntemleri nasıl geçersiz kılınır denetlemek için kullanılır:  
  
|C# değiştiricisi|Tanım|  
|------------------|----------------|  
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|Türetilen bir sınıfta geçersiz kılınmak üzere sınıf üyesine sağlar.|  
|[override](../../../csharp/language-reference/keywords/override.md)|Taban sınıf içinde tanımlı sanal (geçersiz kılınabilir) üyesi geçersiz kılar.|  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|Gerektiren türetilen bir sınıfta geçersiz kılınmak üzere bir sınıf üyesi.|  
|[new Değiştiricisi](../../../csharp/language-reference/keywords/new-modifier.md)|Bir taban sınıftan devralınan üye gizler|  
  
##  <a name="Interfaces"></a> Arabirimleri  
 Sınıfları gibi arabirimler özellikleri, yöntemleri ve olayları kümesini tanımlar. Ancak sınıflarından farklı olarak, uygulama arabirimleri sağlamaz. Bunlar sınıfları tarafından uygulanan ve sınıflardan ayrı varlıklar olarak tanımlanır. Tam olarak tanımlandığı şekilde bir arabirimini uygulayan bir sınıf her açıdan bu arabirimi uygulamalıdır içeren bir sözleşme bir arabirimi temsil eder.  
  
 Bir arabirim tanımlamak için:  
  
```csharp  
interface ISampleInterface  
{  
    void doSomething();  
}  
```  
  
 Bir sınıfta bir arabirim uygulamak için:  
  
```csharp  
class SampleClass : ISampleInterface  
{  
    void ISampleInterface.doSomething()  
    {  
        // Method implementation.  
    }  
}  
```  
  
 Daha fazla bilgi için bkz.:  
  
 [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)  
  
 [interface](../../../csharp/language-reference/keywords/interface.md)  
  
##  <a name="Generics"></a> Genel türler  
 Sınıflar, yapılar, arabirimler ve .NET Framework yöntemlerini içerebilir *tür parametrelerindeki* kullanan depolamak veya nesne türlerini tanımlar. Genel türler en yaygın örneği, bir koleksiyonda depolanan nesnelerin türü belirtebileceğiniz koleksiyonudur.  
  
 Genel bir sınıf tanımlamak için:  
  
```csharp  
public class SampleGeneric<T>   
{  
    public T Field;  
}  
```  
  
 Genel bir sınıf örneği oluşturmak için:  
  
```csharp  
SampleGeneric<string> sampleObject = new SampleGeneric<string>();  
sampleObject.Field = "Sample string";  
```  
  
 Daha fazla bilgi için bkz.:  
  
-   [Genel Türler](~/docs/standard/generics/index.md)  
  
-   [Genel Türler](../../../csharp/programming-guide/generics/index.md)  
  
##  <a name="Delegates"></a> Temsilciler  
 A *temsilci* yöntem imzası tanımlar türüdür ve herhangi bir yöntem başvuru ile uyumlu bir imzası sağlayabilir. Çağırma (çağrı yöntemi temsilci aracılığıyla veya). Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.  
  
> [!NOTE]
>  Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir. Olay işlemede kullanma hakkında daha fazla bilgi için bkz: [olayları](../../../standard/events/index.md).  
  
 Bir temsilciyi oluşturmak için:  
  
```csharp  
public delegate void SampleDelegate(string str);  
```  
  
 Temsilci tarafından belirtilen imza eşleşen bir yöntem başvuru oluşturmak için:  
  
```csharp  
class SampleClass  
{  
    // Method that matches the SampleDelegate signature.  
    public static void sampleMethod(string message)  
    {  
        // Add code here.  
    }  
    // Method that instantiates the delegate.  
    void SampleDelegate()  
    {  
        SampleDelegate sd = sampleMethod;  
        sd("Sample string");  
    }  
}  
```  
  
 Daha fazla bilgi için bkz.:  
  
-   [Temsilciler](../../../csharp/programming-guide/delegates/index.md)  
  
-   [delegate](../../../csharp/language-reference/keywords/delegate.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
