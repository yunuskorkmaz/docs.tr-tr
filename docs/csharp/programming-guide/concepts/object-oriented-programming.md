---
title: Nesne odaklı programlama (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 8f7a810b3f3ec74723ca5e715b7428e1b60928f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702489"
---
# <a name="object-oriented-programming-c"></a>Nesne odaklı programlama (C#)
C#, kapsülleme, devralma ve çok biçimlilik dahil olmak üzere nesne yönelimli programlama için tam destek sağlar.  
  
 *Kapsülleme* ilgili özellikleri, yöntemleri ve diğer üyeleri bir grup işlem tek bir birim veya nesne anlamına gelir.  
  
 *Devralma* mevcut bir sınıfı temel alan yeni sınıflar oluşturma becerisidir.  
  
 *Çok biçimlilik* her sınıf aynı özellikleri veya yöntemleri farklı şekilde uygular olsa da birbirinin yerine kullanılabilen birden fazla sınıfınız olabileceği anlamına gelir.  
  
 Bu bölüm aşağıdaki kavramları açıklar:  
  
-   [Sınıflar ve nesneler](#Classes)  
  
    -   [Sınıf üyeleri](#Members)  
  
         [Özellikler ve alanları](#Properties)  
  
         [Yöntemler](#Methods)  
  
         [Oluşturucular](#Constructors)  
  
         [Sonlandırıcılar](#Finalizers)  
  
         [Olaylar](#Events)  
  
         [İç içe geçmiş sınıflar](#NestedClasses)  
  
    -   [Erişim değiştiricileri ve erişim düzeyleri](#AccessModifiers)  
  
    -   [Sınıf oluşturma](#InstantiatingClasses)  
  
    -   [Statik sınıflar ve Üyeler](#Static)  
  
    -   [Anonim Tipler](#AnonymousTypes)  
  
-   [Devralma](#Inheritance)  
  
    -   [Üyeleri geçersiz kılma](#Overriding)  
  
-   [Arabirimler](#Interfaces)  
  
-   [Genel Türler](#Generics)  
  
-   [Temsilciler](#Delegates)  
  
##  <a name="Classes"></a> Sınıflar ve nesneler  
 Koşulları *sınıfı* ve *nesne* bazen birbirlerinin yerine, ancak aslında sınıfları açıklar kullanılan *türü* nesnelerin nesneleri iken  *örnekleri* sınıf. Bu nedenle, bir nesne oluşturma işlemi olarak da adlandırılır *oluşturmada*. Blueprint benzerliği kullanarak bir sınıf plandır ve nesne bu yapılan bir binadır.  
  
 Bir sınıf tanımlamak için:  
  
```csharp  
class SampleClass  
{  
}  
```  
  
 C# ayrıca sağlayan hafif bir sınıflar adlandırılan sürümünü *yapıları* yapın ve büyük nesneler dizisi oluşturmanız gerektiğinde yararlı olan çok fazla bellek için kullanmak istemiyorsanız.  
  
 Yapı tanımlamak için:  
  
```csharp  
struct SampleStruct  
{  
}  
```  
  
 Daha fazla bilgi için bkz.:  
  
-   [class](../../../csharp/language-reference/keywords/class.md)  
  
-   [struct](../../../csharp/language-reference/keywords/struct.md)  
  
###  <a name="Members"></a> Sınıf üyeleri  
 Her sınıf farklı olabilir *sınıf üyeleri* sınıf verilerini, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasındaki iletişimi sağlayan olayları tanımlayan özellikler içerir.  
  
####  <a name="Properties"></a> Özellikler ve alanları  
 Alanlar ve özellikler bir nesnenin içerdiği bilgileri temsil eder. Bunlar okunabilir ve doğrudan ayarlamak için alanları gibi değişkenlerdir.  
  
 Bir alanı tanımlamak için:  
  
```csharp  
class SampleClass  
{  
    public string sampleField;  
}  
```  
  
 Özellik get ve set yordamları, değerlerin nasıl ayarlanacağı veya döndürüleceği hakkında daha fazla denetim sağlar.  
  
 C# ya da özellik değerini depolamak için özel bir alan oluşturabilir veya bu alanı arka planda otomatik olarak oluşturmak ve özellik yordamları için temel mantığı sağlayan sözde ve otomatik olarak uygulanan özellikler sağlar.  
  
 Otomatik uygulanan bir özellik tanımlamak için:  
  
```csharp  
class SampleClass  
{  
    public int SampleProperty { get; set; }  
}  
```  
  
 Okuma için bazı ek işlemler gerçekleştirebilir ve yazma özellik değeri özellik değerini depolamak için bir alan tanımlayın ve depolanması ve alınması için temel mantığı sağlayan gerekiyorsa:  
  
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
  
 Çoğu özellikleri, yöntemleri ya da yordamlar hem ayarlamak ve özellik değerini almak için vardır. Ancak, değiştiren veya okunmalarını kısıtlamak için salt okunur veya salt yazılır özellikler oluşturabilirsiniz. C# ' ta atlayabilirsiniz `get` veya `set` özellik yöntemi. Ancak, otomatik uygulanan özellikler salt okunur veya salt yazılır olamaz.  
  
 Daha fazla bilgi için bkz.:  
  
-   [get](../../../csharp/language-reference/keywords/get.md)  
  
-   [set](../../../csharp/language-reference/keywords/set.md)  
  
####  <a name="Methods"></a> Yöntemleri  
 A *yöntemi* , nesnenin gerçekleştirebileceği bir eylemdir.  
  
 Bir sınıfın yöntemini tanımlamak için:  
  
```csharp  
class SampleClass  
{  
    public int sampleMethod(string sampleParam)  
    {  
        // Insert code here  
    }  
}  
```  
  
 Bir sınıfta çeşitli uygulamalar olabilir veya *aşırı*, parametre sayıları veya parametre türleri içinde farklı aynı yöntemin.  
  
 Bir yöntemi aşırı yüklemek için:  
  
```csharp  
public int sampleMethod(string sampleParam) {};  
public int sampleMethod(int sampleParam) {}  
```  
  
 Çoğu durumda, sınıf tanımında bir yöntem bildirin. Ancak, ayrıca C# destekler *genişletme yöntemleri* mevcut sınıfa sınıfın gerçek tanımı dışında yöntemler eklemenize olanak tanıyan.  
  
 Daha fazla bilgi için bkz.:  
  
-   [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Genişletme Yöntemleri](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
  
####  <a name="Constructors"></a> Oluşturucular  
 Oluşturucular, belirli bir türde bir nesne oluşturulduğunda, otomatik olarak yürütülen sınıf yöntemleridir. Kurucular genellikle yeni nesnenin veri üyeleri başlatın. Sonra yalnızca bir sınıf oluşturulduğunda Oluşturucu çalıştırabilirsiniz. Ayrıca, Oluşturucudaki kod her zaman bir sınıftaki herhangi bir kod önce çalışır. Ancak, başka bir yöntem olduğu gibi birden çok oluşturucu aşırı yüklemeleri oluşturabilirsiniz.  
  
 Bir sınıf için bir kurucu tanımlamak için:  
  
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
 Sonlandırıcılar, sınıfların örneklerini yok etmek üzere kullanılır. .NET Framework, atık toplayıcı sağlanmasını ve ayrılmasını uygulamanızda yönetilen nesneler için bellek otomatik olarak yönetir. Ancak, yine de sonlandırıcılar uygulamanızın oluşturduğu herhangi yönetilmeyen kaynakları temizlemek için gerekebilir. Yalnızca bir olabilir bir sınıf için bir sonlandırıcı.  
  
 Sonlandırıcılar ve .NET Framework atık toplama hakkında daha fazla bilgi için bkz: [çöp toplama](../../../standard/garbage-collection/index.md).  
  
####  <a name="Events"></a> Olayları  
 Bir sınıf olayları etkinleştirin veya nesneyi diğer sınıfları veya nesneleri ilgilendiğiniz bir şeyler olduğunda gerçekleşir. Olay gönderir (veya harekete geçiren) sınıf adlı *yayımcı* ve olay alma (veya tanıtıcı) sınıflar adlandırılan *aboneleri*. Olaylar hakkında daha fazla bilgi için nasıl oluştukları ve işlendikleri bkz [olayları](../../../standard/events/index.md).  
  
-   Bir sınıf içinde bir olay bildirmek için kullanın [olay](../../../csharp/language-reference/keywords/event.md) anahtar sözcüğü.  
  
-   Bir olayı için olay temsilcisini çağırın.  
  
-   Bir olaya abone olmak için kullanmak `+=` işleci, bir olayın aboneliğini kaldırmak için kullanın; `-=` işleci.  
  
####  <a name="NestedClasses"></a> İç içe geçmiş sınıflar  
 Başka bir sınıfın içinde tanımlanan bir sınıfa *iç içe geçmiş*. Varsayılan olarak, iç içe geçmiş özel sınıftır.  
  
```csharp  
class Container  
{  
    class Nested  
    {  
        // Add code here.  
    }  
}  
```  
  
 İç içe geçmiş sınıfının bir örneğini oluşturmak için kapsayıcı sınıfının arkasına bir nokta koyun ve sonra ardından iç içe geçmiş sınıf adı adını kullanın:  
  
```csharp  
Container.Nested nestedInstance = new Container.Nested()  
```  
  
###  <a name="AccessModifiers"></a> Erişim değiştiricileri ve erişim düzeyleri  
 Tüm sınıflar ve sınıf üyeleri sağlamaları için diğer sınıflar kullanılarak hangi erişim düzeyini belirtebilirsiniz *erişim değiştiricilerine*.  
  
 Aşağıdaki erişim değiştiriciler kullanılabilir:  
  
|C# Modifier|Tanım|  
|------------------|----------------|  
|[public](../../../csharp/language-reference/keywords/public.md)|Türe veya üyeye aynı derlemenin veya ona başvuran başka bir derleme içindeki diğer kodlardan tarafından erişilebilir.|  
|[private](../../../csharp/language-reference/keywords/private.md)|Türe veya üyeye aynı sınıftaki kod tarafından yalnızca erişilebilir.|  
|[protected](../../../csharp/language-reference/keywords/protected.md)|Türe veya üyeye aynı sınıftaki veya türetilmiş bir sınıf içinde kod tarafından yalnızca erişilebilir.|  
|[internal](../../../csharp/language-reference/keywords/internal.md)|Türe veya üyeye aynı derlemedeki ancak farklı derlemeyle herhangi bir kod tarafından erişilebilir.|  
|[protected internal](../../../csharp/language-reference/keywords/protected-internal.md)|Türe veya üyeye aynı derlemedeki kod ile veya başka bir derlemedeki türetilmiş sınıfla erişilebilir.|  
|[private protected](../../../csharp/language-reference/keywords/private-protected.md)|Türe veya üyeye aynı sınıftaki veya türetilmiş bir sınıfın temel sınıf derleme içinde kod tarafından erişilebilir.|  
  
 Daha fazla bilgi için [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
###  <a name="InstantiatingClasses"></a> Sınıf oluşturma  
 Bir nesne oluşturmak için bir sınıf örneği başlatmanız veya sınıf örneği oluşturmanız gerekir.  
  
```csharp  
SampleClass sampleObject = new SampleClass();  
```  
  
 Bir sınıf başlatıldıktan sonra Örneğin özelliklerine ve alanlarına değerler atayın ve sınıf yöntemini çağırabilirsiniz.  
  
```csharp  
// Set a property value.  
sampleObject.sampleProperty = "Sample String";  
// Call a method.  
sampleObject.sampleMethod();  
```  
  
 Sınıf örnekleme işlemi sırasında özellikleri değerleri atamak için nesne başlatıcıları kullanın:  
  
```csharp  
// Set a property value.  
SampleClass sampleObject = new SampleClass   
    { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 Daha fazla bilgi için bkz.:  
  
-   [new İşleci](../../../csharp/language-reference/keywords/new-operator.md)  
  
-   [Nesne ve Koleksiyon Başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
  
###  <a name="Static"></a> Statik sınıflar ve Üyeler  
 Statik sınıf üyesi bir özellik, yordam veya bir sınıfın tüm örnekleri tarafından paylaşıldığını alan var.  
  
 Statik bir üye tanımlamak için:  
  
```csharp  
static class SampleClass  
{  
    public static string SampleString = "Sample String";  
}  
```  
  
 Statik bir üyeye erişmek için sınıfın adını, bu sınıfın bir nesnesi oluşturmadan kullanın:  
  
```csharp  
Console.WriteLine(SampleClass.SampleString);  
```  
  
 C# ' de statik sınıflar yalnızca statik üyeleri sahiptir ve örnekleri oluşturulamaz. Statik üyeleri de statik olmayan özellikler, alanlara veya yöntemlere erişemez  
  
 Daha fazla bilgi için bkz: [statik](../../../csharp/language-reference/keywords/static.md).  
  
###  <a name="AnonymousTypes"></a> Anonim türler  
 Anonim türler nesne veri türü için bir sınıf tanımı yazmaya gerek kalmadan oluşturmanıza olanak sağlar. Bunun yerine, derleyici bir sınıf sizin için oluşturur. Sınıfın kullanılabilir adı yok ve nesneyi bildirirken belirttiğiniz özellikleri içeriyor.  
  
 Anonim bir türün bir örneğini oluşturmak için:  
  
```csharp  
// sampleObject is an instance of a simple anonymous type.  
var sampleObject =   
    new { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 Daha fazla bilgi için bkz.: [Anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
##  <a name="Inheritance"></a> Devralma  
 Devralma, başka bir sınıfta tanımlanan davranışı değiştirir kullanır ve genişleten yeni bir sınıf oluşturmanıza olanak sağlar. Üyeleri devralınan sınıf *temel sınıfı*, ve bu üyeleri devralan sınıf *türetilmiş sınıf*. Ancak, C# içindeki tüm sınıflar örtük olarak devralınacak <xref:System.Object> .NET sınıf hiyerarşisini destekleyen ve tüm sınıflara alt düzey hizmetler sağlayan sınıf.  
  
> [!NOTE]
>  C# birden çok devralmayı desteklemez. Diğer bir deyişle, türetilmiş bir sınıf için yalnızca bir temel sınıf belirtebilirsiniz.  
  
 Temel sınıfından devralmak için:  
  
```csharp  
class DerivedClass:BaseClass {}  
```  
  
 Varsayılan olarak, tüm sınıflar devralınabilir. Ancak, bir sınıfın temel sınıf olarak kullanılmamalıdır veya yalnızca temel sınıf olarak kullanılan bir sınıf oluşturmak olup olmadığını belirtebilirsiniz.  
  
 Bir sınıfın temel sınıf olarak kullanılamayacağını belirtmek için:  
  
```csharp  
public sealed class A { }  
```  
  
 Bir sınıf yalnızca temel sınıf olarak kullanılabilecek ve başlatılamayacak belirtmek için:  
  
```csharp  
public abstract class B { }  
```  
  
 Daha fazla bilgi için bkz.:  
  
-   [sealed](../../../csharp/language-reference/keywords/sealed.md)  
  
-   [abstract](../../../csharp/language-reference/keywords/abstract.md)  
  
###  <a name="Overriding"></a> Üyeleri geçersiz kılma  
 Varsayılan olarak, türetilmiş bir sınıf tüm üyelerini kendi temel sınıfından devralır. Devralınan üye davranışını değiştirmek istiyorsanız, onu geçersiz kılmanız gerekir. Diğer bir deyişle, türetilmiş bir sınıf içindeki yöntemin, özelliğin veya olayın yeni bir uygulamasını tanımlayabilirsiniz.  
  
 Özellikleri ve yöntemleri nasıl geçersiz kılınacağını denetlemek için aşağıdaki değiştiriciler kullanılır:  
  
|C# Modifier|Tanım|  
|------------------|----------------|  
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|Bir sınıf üyesinin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.|  
|[override](../../../csharp/language-reference/keywords/override.md)|Temel sınıfta tanımlanan sanal bir (geçersiz kılınabilir) üyeyi geçersiz kılar.|  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|Gerektiren bir sınıf üyesinin derlenen sınıfta geçersiz kılınacak.|  
|[new Değiştiricisi](../../../csharp/language-reference/keywords/new-modifier.md)|Bir temel sınıftan devralınan üyeyi gizler|  
  
##  <a name="Interfaces"></a> Arabirimleri  
 Sınıflar gibi arabirimler, özellikleri, yöntemleri ve olayları kümesi tanımlarsınız. Ancak, sınıflardan farklı olarak, arabirimler uygulama sağlamaz. Bunlar sınıfları tarafından uygulanır ve sınıflardan ayrı varlıklar olarak tanımlanır. Tam olarak tanımlandığı şekilde bir arabirimi uygulayan bir sınıf, o arabirimi her yönüyle uygulamalıdır bir arabirim bir sözleşmeyi temsil eder.  
  
 Arabirim tanımlamak için:  
  
```csharp  
interface ISampleInterface  
{  
    void doSomething();  
}  
```  
  
 Bir sınıf içinde arabirim uygulamak için:  
  
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
 Sınıflar, yapılar, arabirimler ve yöntemler .NET Framework'teki içerebilir *tür parametrelerindeki* bunlar depolayabildikleri veya kullanabildikleri nesnelerin türlerini tanımlayan. Genel türlerin yararları en yaygın örnek, bir koleksiyonda depolanacak nesnelerin türünü belirleyebileceğiniz koleksiyonudur.  
  
 Genel bir sınıf tanımlamak için:  
  
```csharp  
public class SampleGeneric<T>   
{  
    public T Field;  
}  
```  
  
 Bir genel sınıfın bir örneğini oluşturmak için:  
  
```csharp  
SampleGeneric<string> sampleObject = new SampleGeneric<string>();  
sampleObject.Field = "Sample string";  
```  
  
 Daha fazla bilgi için bkz.:  
  
-   [Genel Türler](~/docs/standard/generics/index.md)  
  
-   [Genel Türler](../../../csharp/programming-guide/generics/index.md)  
  
##  <a name="Delegates"></a> Temsilciler  
 A *temsilci* , yöntem imzasını tanımlayan bir türdür ve uyumlu bir imza ile herhangi bir yönteme başvuru sağlayabilir. Çağırma (çağrı yöntemi temsilci aracılığıyla veya). Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.  
  
> [!NOTE]
>  Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir. Temsilcileri olay işlemede kullanma hakkında daha fazla bilgi için bkz. [olayları](../../../standard/events/index.md).  
  
 Temsilci oluşturmak için:  
  
```csharp  
public delegate void SampleDelegate(string str);  
```  
  
 Temsilci tarafından belirtilen imzayla eşleşen bir yönteme başvuru oluşturmak için:  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
