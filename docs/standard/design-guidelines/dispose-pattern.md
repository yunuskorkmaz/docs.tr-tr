---
title: Dispose deseni
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff52e17cfe4a4236e4d165c0961ca3a23fed9a72
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864650"
---
# <a name="dispose-pattern"></a>Dispose deseni
Tüm Programlar kursu, yürütme sırasında bir veya daha fazla sistem kaynakları, bellek, sistemi işleyicilerini veya veritabanı bağlantıları gibi edinin. Geliştiriciler alınan ve kullanılan sonra bunlar serbest bırakılması gerekir çünkü bu tür sistem kaynakları kullanırken dikkatli olmanız gerekir.  
  
 CLR'nin otomatik bellek yönetimi için destek sağlar. Yönetilen bellek (C# işleci kullanılarak ayrılmış bellek `new`) açıkça serbest bırakılması gerekmez. Atık toplayıcı (GC) tarafından otomatik olarak yayımlanır. Bu işlem, bellek serbest zor ve yorucu bir görev geliştiricilerden serbest bırakır ve .NET Framework tarafından gösterilen eşi görülmemiş bir üretkenlik için temel nedenlerinden biri olmuştur.  
  
 Ne yazık ki, yönetilen bellek yalnızca sistem kaynakları birçok türde biridir. Yönetilen bellek haricinde kaynaklar yine de açıkça serbest bırakılması gerektiği ve yönetilmeyen kaynaklar olarak adlandırılır. GC yönetilmeyen gibi kaynakları yönetmek için yönetilmeyen kaynaklarını yönetme sorumluluğunu geliştiricilere elinizde kaynaklandığını anlamına gelir tasarlanmamıştır özellikle.  
  
 CLR yönetilmeyen kaynakları serbest bırakmak bazı Yardım sağlar. <xref:System.Object?displayProperty=nameWithType> sanal yöntem <xref:System.Object.Finalize%2A> (Sonlandırıcı olarak da bilinir) adlı atık toplama tarafından önce nesnenin bellek atık toplama tarafından geri kazanılır ve yönetilmeyen kaynakları serbest bırakmak için geçersiz kılınabilir. Sonlandırıcıyı geçersiz kılın türleri sonlandırılabilir türleri olarak adlandırılır.  
  
 Sonlandırıcılar bazı temizleme senaryolarda etkili olsa da, bunlar iki önemli engelleri vardır:  
  
-   Atık toplama bir nesne koleksiyonu için uygun olduğunu algıladığında, sonlandırıcı adı verilir. Bu, belirli belirsiz bir süre sonra kaynak artık gerekli değildir gerçekleşir. Olduğunda Geliştirici olabilir veya kaynak ve zaman Sonlandırıcı tarafından kaynak gerçekten yayınlandığında serbest bırakmak istediğiniz arasında gecikme çok nadir kaynakları (kolayca bitti kaynaklar) elde ettiğiniz programlar ya da kabul edilemez olabilir. Kaynakları (örneğin, büyük bir yönetilmeyen bellek arabellek) kullanımda tutmak pahalı olduğu durumlarda.  
  
-   CLR bir sonlandırıcı çağrısı gerektiğinde, sonraki yuvarlak çöp toplama (koleksiyonları arasında çalıştırma sonlandırıcılar) kadar nesnenizin belleğini koleksiyonunu erteleme gerekir. Bu, nesnenizin belleğini (ve başvurduğu tüm nesneler) daha uzun bir süre için kullanıma sunulacağını yok anlamına gelir.  
  
 Bu nedenle, bağlı olan özel sonlandırıcılar üzerinde yönetilmeyen kaynakları nadir kaynakları ile ilgilenirken, mümkün olan en kısa sürede geri kazanmak önemli olduğu durumlarda birçok senaryoda ya da yüksek performanslı senaryolarında, uygun olmayabilir eklenen GC ek yükü sonlandırma kabul edilebilir değil.  
  
 Bir çerçeve sağlar <xref:System.IDisposable?displayProperty=nameWithType> Geliştirici gerekli olmayan hemen sonra yönetilmeyen kaynaklar serbest bırakılacaksa el ile bir yol sağlamak için uygulanması gereken Arabirimi. Ayrıca sağlar <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> GC, söyleyebilirsiniz yöntemi bir nesne, el ile bırakıldı ve artık sonlandırılmayı nesnenizin belleğini daha önce bu durumda kazanılabilir gerek yoktur. Türleri uygulayan `IDisposable` arabirimi atılabilir türler adlandırılır.  
  
 Dispose deseni kullanım ve sonlandırıcılar uygulaması standart hale getirmek için tasarlanmıştır ve `IDisposable` arabirimi.  
  
 Desen ana hacktivism yürütmesinin karmaşıklığını azaltmaktır <xref:System.Object.Finalize%2A> ve <xref:System.IDisposable.Dispose%2A> yöntemleri. Gelen yöntemleri (farklar, sonraki bölümde açıklanmıştır) ancak tüm kod yolları paylaşmak olgu karmaşıklığı kaynaklanır. Ayrıca, bazı öğeler evrimi belirleyici kaynak yönetimi için dil desteği, ilgili Düzen geçmiş nedeni vardır.  
  
 **✓ DO** atılabilir türler örneklerini içeren türlerinde temel Dispose desenini uygular. Bkz: [temel Dispose deseni](#basic_pattern) bölümde temel düzeni hakkında ayrıntılı bilgi için.  
  
 Bir tür atılabilen diğer nesnelerin ömrü boyunca sorumlu geliştiriciler, çok silmek için bir yol gerekir. Kapsayıcının kullanarak `Dispose` bunu mümkün hale getirmek için kullanışlı bir yol yöntemidir.  
  
 **✓ DO** temel Dispose desen uygulamak ve bir sonlandırıcı türlerinde, açıkça boşaltılması gerekiyor ve sonlandırıcılar sahip değil tutan kaynakları sağlar.  
  
 Örneğin, deseni, yönetilmeyen bellek arabelleği depolama türlerinde uygulanmalıdır. [Sonlandırılabilir türleri](#finalizable_types) bölümde, bir sonlandırıcı uygulamak için ilgili yönergeler açıklanmaktadır.  
  
 **✓ CONSIDER** temel Dispose düzeni uygulama sınıflarında kendilerini tutmayın yönetilmeyen kaynakları veya tek kullanımlık nesneleri ancak yapmak subtypes etkileyebilir.  
  
 Bu harika bir örneği <xref:System.IO.Stream?displayProperty=nameWithType> sınıfı. Tüm kaynakları tutan değil Özet temel sınıf olmasına rağmen alt sınıflara çoğunu ve bu nedenle, bu deseni uygular.  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a>Temel Dispose deseni  
 Uygulama düzeninin basit uygulaması içerir `System.IDisposable` arabirimi ve bildirme `Dispose(bool)` arasında paylaşılması için tüm kaynak temizleme mantığını uygulayan yöntemi `Dispose` yöntemi ve isteğe bağlı bir sonlandırıcı.  
  
 Aşağıdaki örnek, basit bir uygulama temel deseni gösterir:  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder() {  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose() {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing) {  
        if (disposing) {  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 Boole parametresi `disposing` gelen yöntemi çağrıldı olup olmadığını gösteren `IDisposable.Dispose` uygulama veya Sonlandırıcı. `Dispose(bool)` Diğer başvuru nesneleri (örneğin, yukarıdaki örnekte kaynak alan) erişmeden önce uygulama parametresi denetlemelidir. Gelen yöntem çağrıldığında bu tür nesneler yalnızca erişilen `IDisposable.Dispose` uygulama (zaman `disposing` parametresi true olarak eşittir). Yöntemin Sonlandırıcı çağrılması durumunda (`disposing` false), diğer nesnelerin erişilemiyor. Nesneler beklenmedik bir sırada olan sonlandırılır ve bu nedenle bunlar ve bunların bağımlılıklarını hiçbirini zaten sonlandırılan nedenidir.  
  
 Ayrıca, bu bölüm, zaten Dispose desenini uygulamaz tabana sahip sınıflar için geçerlidir. Desen uygulayan bir sınıftan devraldığını ise yalnızca geçersiz kılma `Dispose(bool)` ek kaynak temizleme mantığını sağlamak için yöntemi.  
  
 **✓ DO** bildirme bir `protected virtual void Dispose(bool disposing)` tüm mantığı merkezileştirmek yöntemi ilgili yönetilmeyen kaynakları serbest bırakma için.  
  
 Bu yöntemde tüm kaynak temizleme gerçekleşmelidir. Yöntem sonlandırıcıyı çağrılır ve `IDisposable.Dispose` yöntemi. Parametre bir sonlandırıcı içinde çağrılan yanlış olur. Sonlandırma sırasında çalışan herhangi bir kod sonlandırılabilir diğer nesnelerin erişilmemesi emin olmak için kullanılmalıdır. Sonlandırıcılar uygulama ayrıntılarını, sonraki bölümde açıklanmıştır.  
  
```csharp
protected virtual void Dispose(bool disposing) {  
    if (disposing) {  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 **✓ DO** uygulamak `IDisposable` yalnızca çağırarak arabirim `Dispose(true)` arkasından `GC.SuppressFinalize(this)`.  
  
 Çağrı `SuppressFinalize` yalnızca durumunda gerçekleşmesi gereken `Dispose(true)` başarılı bir şekilde yürütür.  
  
```csharp
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 **X DO NOT** parametresiz olun `Dispose` sanal yöntemi.  
  
 `Dispose(bool)` Alt sınıflar tarafından geçersiz kılınması gereken bir yöntemdir.  
  
```csharp
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose() { ... }  
    protected virtual void Dispose(bool disposing) { ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose() { ... }  
    protected virtual void Dispose(bool disposing) { ... }  
}  
```  
  
 **X DO NOT** hiçbir aşırı bildirme `Dispose` yöntemi dışında `Dispose()` ve `Dispose(bool)`.  
  
 `Dispose` Bu düzen kod oluşturma ve uygulayıcılar, kullanıcılar ve derleyiciler arasındaki Karışıklığı önlemek için ayrılmış bir sözcük düşünülmelidir. Bazı diller, otomatik olarak bu deseni belirli türlerde uygulamak seçebilirsiniz.  
  
 **✓ DO** izin `Dispose(bool)` birden çok kez çağrılacak yöntem. Yöntemi, hiçbir şey yapma ilk çağrıdan sonra da tercih edebilirsiniz.  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing) {  
        if (disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **X AVOID** içinden bir özel durum atma `Dispose(bool)` dışındaki burada içeren işlem bozulmuş Kritik durumları altında (sızıntılarını, paylaşılan durumu tutarsız, vs.).  
  
 Kullanıcıların beklediğiniz bir çağrı `Dispose` bir özel durum oluşturmaz.  
  
 Varsa `Dispose` bir özel durum oluşturabilen, daha fazla finally bloğu temizleme mantıksal değil yürütülecek. Bu sorunu çözmek için kullanıcının yapılan her çağrı kaydırma gerekir `Dispose` (içinde finally bloğunda!) bir try bloğunda, müşteri adayları için çok karmaşık temizleme işleyicileri. Çalıştırıldığında bir `Dispose(bool disposing)` yöntemi, hiçbir zaman throw disposing false ise özel durumu. Bunun yapılması bir sonlandırıcı bağlamı içinde çalıştırıldığında işlemini sonlandırır.  
  
 **✓ DO** throw bir <xref:System.ObjectDisposedException> , nesne atıldı sonra kullanılamayan üyeden.  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething() {  
        if (disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
        ...  
    }  
    protected virtual void Dispose(bool disposing) {  
        if (disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **✓ CONSIDER** yöntemi sağlama `Close()`, ek olarak `Dispose()`, yakın alan standart terminolojisinde olup olmadığını.  
  
 Bunun yapılması, yaptığınız önemli olduğu `Close` aynı uygulama `Dispose` ve uygulamayı düşünün `IDisposable.Dispose` yöntemi açıkça.  
  
```csharp
public class Stream : IDisposable {  
    IDisposable.Dispose() {  
        Close();  
    }  
    public void Close() {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## <a name="finalizable-types"></a>Sonlandırılabilir türleri  
 Sonlandırılabilir türler sonlandırıcıyı geçersiz kılma ve sonlandırma kod yolunda sağlayarak temel Dispose desenini genişleten türler `Dispose(bool)` yöntemi.  
  
 Öncelikle, belirli (normalde geçerli) sistem durumu hakkında yürütülmesi sırasında varsayımlar yapamazsınız çünkü sonlandırıcılar doğru uygulamak öğesinin zordur. Aşağıdaki yönergeleri dikkatle dikkate alınması.  
  
 Bazı yönergeler için değil yalnızca geçerli olduğunu unutmayın `Finalize` yöntemi, ancak herhangi bir kod için bir sonlandırıcı çağrılır. İçinde yürüten mantığı temel Dispose önceden tanımlanmış düzeni söz konusu olduğunda, yani `Dispose(bool disposing)` olduğunda `disposing` parametre değer false.  
  
 Temel sınıf zaten sonlandırılabilir ve temel Dispose desenini uygular, değil'ı geçersiz kılmalıdır `Finalize` yeniden. Yalnızca kılmanız gereken `Dispose(bool)` ek kaynak temizleme mantığını sağlamak için yöntemi.  
  
 Aşağıdaki kod örneği sonlandırılabilir türü gösterir:  
  
```csharp
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder() {  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing) {  
            ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing) { // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ComplexResourceHolder() {
        Dispose(false);  
    }  
  
    public void Dispose() {
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 **X AVOID** türleri sonlandırılabilir yapma.  
  
 Bir sonlandırıcı gerekli düşündüğünüz herhangi bir durumu dikkatlice düşünün. Gerçek yoktur, hem performans hem de kod karmaşıklık açısından sonlandırıcılar örnekleriyle ilişkili maliyeti. Kaynak sarmalayıcıları gibi kullanmayı tercih <xref:System.Runtime.InteropServices.SafeHandle> mümkün olduğunda yönetilmeyen kaynakları kapsüllemek üzere bu durumda bir sonlandırıcı olur gereksiz sarmalayıcı kendi kaynak Temizleme için sorumlu olduğu için.  
  
 **X DO NOT** değer türleri sonlandırılabilir olun.  
  
 Yalnızca başvuru türleri CLR tarafından gerçekten kesin ve bu nedenle bir değer türü üzerinde bir sonlandırıcı yerleştirmek için her türlü girişim yok sayılacak. C# ve C++ Derleyicileri, bu kuralı uygular.  
  
 **✓ DO** tür kendi Sonlandırıcı olmayan bir yönetilmeyen kaynak serbest bırakma için sorumlu ise bir türü sonlandırılabilir olun.  
  
 Bir sonlandırıcı uygulamak, yalnızca çağrı `Dispose(false)` ve içindeki tüm kaynak temizleme mantığını yerleştirin `Dispose(bool disposing)` yöntemi.  
  
```csharp
public class ComplexResourceHolder : IDisposable {  
  
    ~ComplexResourceHolder() {
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing) {
        ...  
    }  
}  
```  
  
 **✓ DO** her sonlandırılabilir türüne temel Dispose desenini uygular.  
  
 Bu kullanıcıların türü açıkça Sonlandırıcı sorumlu olduğu aynı bu kaynakların belirlenimci temizleme gerçekleştirmek için bir yol sağlar.  
  
 **X DO NOT** önemli riski Bunlar zaten sonlandırılan, çünkü sonlandırıcıyı kod yolunda sonlandırılabilir tüm nesnelere erişme.  
  
 Örneğin, bir başvuru yapan başka bir nesneye sonlandırılabilir B sonlandırılabilir bir nesnenin bir güvenilir bir şekilde B A içinde kullanamazsınız, sonlandırıcı ya da tam tersi. Sonlandırıcılar (kısıtlıysa, kritik sonlandırma bir zayıf sıralama garantisi) rastgele sırayla çağrılır.  
  
 Ayrıca, bir uygulama etki alanı kaldırma sırasında veya işlem sonlandırma sırasında bazı noktalarda statik değişkenlerinde depolanan nesnelerin da toplanan olduğunu unutmayın. Sonlandırılabilir bir nesnenin (veya statik değişkenlerinde depolanan değerleri kullanabilecek statik bir yöntemi) başvurduğu bir statik değişken olmayabilir erişme güvenli if <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> true değerini döndürür.  
  
 **✓ DO** olun, `Finalize` korumalı yöntemi.  
  
 Derleyiciler bu anlayışın zorlamak için yardımcı olduğundan geliştiricilerin C#, C++ ve VB.NET bu konuda endişelenmeniz gerekmez.  
  
 **X DO NOT** let özel durumlar kaçış sistem kritik hataları dışında Sonlandırıcısı mantığı gelen.  
  
 Bir sonlandırıcı bir özel durum, CLR (itibariyle .NET Framework sürüm 2.0), tüm işlem kapatır yürütme ve denetimli bir biçimde yayımlanan kaynakları diğer sonlandırıcılar engelleyen.  
  
 **✓ CONSIDER** oluşturma ve kritik sonlandırılabilir nesnesini kullanarak (içeren bir tür hiyerarşisinde bir türüyle <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) içinde bir sonlandırıcı kesinlikle gerekir yürütme zorlanmış uygulama etki alanı kaldırır ve iş parçacığı karşısında bile durumlar için durdurur.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
- [Ortak Tasarım Desenleri](../../../docs/standard/design-guidelines/common-design-patterns.md)  
- [Atık Toplama](../../../docs/standard/garbage-collection/index.md)
