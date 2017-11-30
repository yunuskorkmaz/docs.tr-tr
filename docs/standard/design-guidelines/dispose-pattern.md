---
title: Desen dispose
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 97f0c63857b7af408613e1ffdfecb157d1e2c704
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="dispose-pattern"></a>Desen dispose
Tüm Programlar bir veya daha fazla sistem kaynakları, bellek, sistem tanıtıcıları veya veritabanı bağlantıları gibi kendi yürütme sürecinde alın. Geliştiriciler alınan ve kullanılan sonra bunlar serbest gerekir çünkü bu tür sistem kaynaklarını kullanırken dikkatli olmanız gerekir.  
  
 CLR otomatik bellek yönetimi için destek sağlar. Yönetilen bellek (C# işleci kullanılarak ayrılmış bellek `new`) açıkça serbest bırakılacak gerekmez. Ayrıca, atık toplayıcı (GC) tarafından otomatik olarak yayımlanır. Bu bellek yayınlama yorucu ve zor görev geliştiricilerden boşaltır ve .NET Framework tarafından karşılanan eşi görülmemiş üretkenlik ana nedenlerinden biri olmuştur.  
  
 Ne yazık ki, yönetilen bellek yalnızca sistem kaynaklarını birçok türdeki biridir. Yönetilen bellek dışındaki kaynaklar hala açıkça yayımlanması gerekir ve yönetilmeyen kaynaklar olarak adlandırılır. GC yönetilmeyen gibi kaynakları yönetmek için yönetilmeyen kaynakları yönetmek için sorumluluk geliştiriciler elinizde arasındadır yani tasarlanmamıştır özellikle.  
  
 CLR yönetilmeyen kaynakları serbest bırakma bazı Yardım sağlar. <xref:System.Object?displayProperty=nameWithType>sanal bir yöntem bildirir <xref:System.Object.Finalize%2A> (sonlandırıcıyı olarak da bilinir) çağrılan tarafından GC önce nesnenin bellek tarafından GC iadesi ve yönetilmeyen kaynakları serbest bırakmak için geçersiz kılınabilir. Sonlandırıcıyı geçersiz türleri sonlandırılabilir türleri olarak adlandırılır.  
  
 Sonlandırıcılar bazı temizleme senaryolarda etkili olsa da, bunlar iki önemli sakıncaları vardır:  
  
-   GC bir nesne koleksiyonu için uygun olduğunu algıladığında sonlandırıcıyı adı verilir. Bu, belirli belirlenmemiş bir süre sonra kaynak artık gerekli değildir gerçekleşir. Olduğunda Geliştirici verebilir veya kaynak ve kaynak sonlandırıcıyı tarafından gerçekten zaman yayımlanan saat serbest bırakmak istediğiniz arasındaki gecikme birçok olması kaynakları (kolayca tükendi kaynakları) almayı programlarda veya olarak kabul edilebilir Kaynakları (örneğin, büyük yönetilmeyen bellek arabellek) kullanımda tutmak maliyetli durumları.  
  
-   CLR bir sonlandırıcı çağırmak gerektiğinde sonraki yuvarlamak atık toplama (koleksiyonları arasında çalıştırmak sonlandırıcılar) kadar nesnenin bellek koleksiyonunu erteleyin gerekir. Bu nesnenin bellek (ve başvurduğu tüm nesneler) daha uzun bir süre için serbest bırakılacak değil, anlamına gelir.  
  
 Bu nedenle, özel olarak sonlandırıcılar üzerinde bağlı olan yönetilmeyen kaynakları olması kaynaklarla ilgilenirken mümkün olan en kısa sürede geri kazanmak önemli olduğu durumlarda birçok senaryo ya da yüksek oranda kullanıcı senaryoları uygun olmayabilir eklenen GC ek yükü sonlandırma kabul edilebilir değil.  
  
 Bir çerçeve sağlar <xref:System.IDisposable?displayProperty=nameWithType> Geliştirici gerekli olmadığında hemen yönetilmeyen kaynakları serbest bırakmak için el ile bir yol sağlamak üzere uygulanmalıdır arabirimi. Ayrıca sağlar <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> GC, anlayabilirsiniz yöntemi bir nesne, el ile bırakıldı ve artık, sonlandırılır ve bu durumda nesnenin bellek önceki istenemiyor gerekmez. Türleri uygulayan `IDisposable` arabirimi atılabilir türler olarak adlandırılır.  
  
 Dispose düzeni kullanım ve sonlandırıcılar uyarlamasını standart hale getirmek için tasarlanmıştır ve `IDisposable` arabirimi.  
  
 Uygulaması karmaşıklığını azaltmak için desen ana gerekçesi olan <xref:System.Object.Finalize%2A> ve <xref:System.IDisposable.Dispose%2A> yöntemleri. Yöntemler (farklar sonraki bölümde açıklanmıştır) bazı ancak tüm kod yollarının paylaşmak olgu gelen karmaşıklık kaynaklandığını. Ayrıca, bazı öğeler belirleyici kaynak yönetimi için dil desteği evrimi ilgili deseninin geçmiş nedenleri vardır.  
  
 **✓ YAPMAK** atılabilir türler örneklerini içeren türlerinde temel Dispose desenini uygular. Bkz: [temel Dispose düzeni](#basic_pattern) temel düzeni hakkında ayrıntılı bilgi için bölüm.  
  
 Bir tür atılabilir diğer nesnelerin ömrü boyunca sorumlu ise, geliştiriciler bunlarla ilgili çok silmek için bir yönteme ihtiyacınız vardır. Kapsayıcının kullanarak `Dispose` yöntemi bu mümkün kılmak için uygun bir yoldur.  
  
 **✓ YAPMAK** temel Dispose desen uygulamak ve bir sonlandırıcı türlerinde, açıkça boşaltılması gerekiyor ve sonlandırıcılar sahip değil tutan kaynakları sağlar.  
  
 Örneğin, yönetilmeyen bellek arabelleği depolama türlerinde düzeni uygulanmalıdır. [Sonlandırılabilir türleri](#finalizable_types) bölüm sonlandırıcılar uygulama için ilgili yönergeleri ele alınmaktadır.  
  
 **✓ DÜŞÜNÜN** temel Dispose düzeni uygulama sınıflarında kendilerini tutmayın yönetilmeyen kaynakları veya tek kullanımlık nesneleri ancak yapmak subtypes etkileyebilir.  
  
 Bu harika bir örneği <xref:System.IO.Stream?displayProperty=nameWithType> sınıfı. Herhangi bir kaynağa sahip olmayan bir Özet temel sınıf olmasına rağmen kendi alt sınıfların çoğunu ve bu nedenle, bu deseni uygular.  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a>Temel Dispose düzeni  
 Uygulama deseni temel uyarlamasını içerir `System.IDisposable` arabirimi ve bildirme `Dispose(bool)` arasında paylaşılması için tüm kaynak temizleme mantığını uygulayan yöntemi `Dispose` yöntemi ve isteğe bağlı Sonlandırıcı.  
  
 Aşağıdaki örnekte basit bir uygulama temel deseninin gösterir:  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder(){  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        if (disposing){  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 Boole parametresi `disposing` yöntemi gelen çağrıldı olup olmadığını gösteren `IDisposable.Dispose` uygulaması veya sonlandırıcıyı. `Dispose(bool)` Diğer başvuru nesneleri (örneğin, yukarıdaki örnekteki kaynak alanı) erişmeden önce uygulama parametresi denetlemelidir. Gelen yöntem çağrıldığında bu tür nesneler yalnızca erişilen `IDisposable.Dispose` uygulaması (zaman `disposing` parametresi true değerine eşittir). Sonlandırıcıyı yöntemi çağrıldıysa (`disposing` false), diğer nesneleri değil erişilmelidir. , Nesneler öngörülemeyen bir sırada sonlandırılır ve bu nedenle bunlar veya onların bağımlılıkları hiçbirini zaten sonlandırılan nedenidir.  
  
 Ayrıca, bu bölümde, zaten Dispose düzeni uygulamıyor bir taban sınıflarıyla uygular. Zaten deseni uygulayan bir sınıftan devralmayı, yalnızca geçersiz kılma `Dispose(bool)` yöntemi ek kaynak temizleme mantığı sağlar.  
  
 **✓ YAPMAK** korumalı sanal void bildirme `Dispose(bool disposing)` tüm mantığı merkezileştirmek yöntemi ilgili yönetilmeyen kaynakları serbest bırakma için.  
  
 Tüm kaynak temizleme Bu yöntemde olmalıdır. Yöntem sonlandırıcıyı çağrılır ve `IDisposable.Dispose` yöntemi. Parametre bir sonlandırıcı içinde çağrılan varsa false olur. Sonlandırma sırasında çalıştıran herhangi bir kod sonlandırılabilir diğer nesneleri erişilmemesi emin olmak için kullanılmalıdır. Sonlandırıcılar uygulama ayrıntılarını sonraki bölümde açıklanmaktadır.  
  
```  
protected virtual void Dispose(bool disposing){  
    if (disposing){  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 **✓ YAPMAK** uygulamak `IDisposable` yalnızca çağırarak arabirim `Dispose(true)` arkasından `GC.SuppressFinalize(this)`.  
  
 Çağrı `SuppressFinalize` varsa yalnızca gerçekleşeceğini `Dispose(true)` başarıyla yürütür.  
  
```  
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 **X yok** parametresiz olun `Dispose` sanal yöntemi.  
  
 `Dispose(bool)` Alt sınıflar tarafından geçersiz kılınması gereken bir yöntemdir.  
  
```  
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
```  
  
 **X yok** hiçbir aşırı bildirme `Dispose` yöntemi dışında `Dispose()` ve `Dispose(bool)`.  
  
 `Dispose`Bu desen kod oluşturma ve uygulayıcılar, kullanıcılar ve derleyicileri arasında Karışıklığı önlemek için ayrılmış bir sözcük dikkate alınmalıdır. Bazı diller belirli türlerinde bu deseni otomatik olarak uygulamak seçebilirsiniz.  
  
 **✓ YAPMAK** izin `Dispose(bool)` birden çok kez çağrılacak yöntem. Yöntemi, hiçbir şey ilk çağrısından sonra yapmayı seçebilirsiniz.  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **KAÇININ x** içinden bir özel durum atma `Dispose(bool)` dışındaki burada içeren işlem bozulmuş Kritik durumları altında (sızıntılarını, paylaşılan durumu tutarsız, vs.).  
  
 Kullanıcıların beklediğiniz yapılan bir çağrı `Dispose` bir özel durum oluşturmaz.  
  
 Varsa `Dispose` bir özel durum oluşturabilen, daha fazla finally bloğu temizleme mantığı değil yürütülecek. Bu sorunu çözmek için kullanıcının her çağrı için Kaydır gerekir `Dispose` (içinde finally bloğunda!) bir try bloğunda, müşteri adayları çok karmaşık temizleme işleyicilerine. Çalıştırıldığında bir `Dispose(bool disposing)` yöntemi, hiçbir zaman throw bir atma false ise özel durumu. Bunun yapılması bir Sonlandırıcısı bağlamı içinde çalıştırıldığında işlemini sonlandırır.  
  
 **✓ YAPMAK** throw bir <xref:System.ObjectDisposedException> , nesne atıldı sonra kullanılamayan üyeden.  
  
```  
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething(){  
           if(disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
            ...  
    }  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **✓ DÜŞÜNÜN** yöntemi sağlama `Close()`, ek olarak `Dispose()`, yakın alan standart terminolojisinde olup olmadığını.  
  
 Bunu yaparken, yaptığınız önemli `Close` uygulaması aynı `Dispose` ve uygulayın `IDisposable.Dispose` yöntemi açıkça.  
  
```  
public class Stream : IDisposable {  
    IDisposable.Dispose(){  
        Close();  
    }  
    public void Close(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## <a name="finalizable-types"></a>Sonlandırılabilir türleri  
 Sonlandırılabilir türler sonlandırıcıyı geçersiz kılma ve bir sonlandırma kod yolunda sağlayarak temel Dispose düzeni genişleten türleridir `Dispose(bool)` yöntemi.  
  
 Öncelikle, yürütme sırasında sistem durumuyla ilgili (normalde geçerli) bazı varsayımlarda yapılamıyor çünkü sonlandırıcılar doğru uygulamak notoriously zordur. Aşağıdaki yönergeler dikkatli dikkate almanız.  
  
 Bazı yönergeler için değil yalnızca geçerli olduğunu unutmayın `Finalize` yöntemi, ancak herhangi bir kod için bir sonlandırıcı çağrılır. Temel Dispose önceden tanımlanmış düzeni söz konusu olduğunda, yani içinde yürütür mantığı `Dispose(bool disposing)` zaman `disposing` parametre değer false.  
  
 Taban sınıf zaten sonlandırılabilir ise ve temel Dispose deseni uygular, değil kılmanız `Finalize` yeniden. Bunun yerine yalnızca kılmalıdır `Dispose(bool)` yöntemi ek kaynak temizleme mantığı sağlar.  
  
 Aşağıdaki kod bir sonlandırılabilir türünün bir örneği gösterir:  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder(){  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing){  
            ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing){ // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 **KAÇININ x** türleri sonlandırılabilir yapma.  
  
 Bir sonlandırıcı gerekli düşündüğünüz herhangi bir durumu dikkatlice düşünün. Gerçek yoktur hem performans hem de kod karmaşıklık açısından sonlandırıcılar örnekleriyle ilişkili maliyeti. Kaynak sarmalayıcıları gibi kullanmayı tercih <xref:System.Runtime.InteropServices.SafeHandle> mümkün olduğunda yönetilmeyen kaynakları kapsüllemek için; bu durumda bir sonlandırıcı hale gereksiz sarmalayıcı kendi kaynak Temizleme için sorumlu olduğu için.  
  
 **X yok** değer türleri sonlandırılabilir olun.  
  
 Yalnızca başvuru türleri gerçekte CLR tarafından sonlandırılır ve bu nedenle değer türünde bir sonlandırıcı yerleştirmek için her türlü girişim yok sayılacak. Bu kural, C# ve C++ Derleyicileri uygulayın.  
  
 **✓ YAPMAK** tür kendi Sonlandırıcı olmayan bir yönetilmeyen kaynak serbest bırakma için sorumlu ise bir türü sonlandırılabilir olun.  
  
 Sonlandırıcıyı uygularken, yalnızca çağrısı `Dispose(false)` ve içindeki tüm kaynak temizleme mantığını yerleştirin `Dispose(bool disposing)` yöntemi.  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        ...  
    }  
}  
```  
  
 **✓ YAPMAK** her sonlandırılabilir türüne temel Dispose desenini uygular.  
  
 Bu türdeki kullanıcıların açıkça belirleyici temizleme sonlandırıcıyı sorumlu olduğu kaynaklarla işlemini gerçekleştirmek için bir yol sağlar.  
  
 **X yok** önemli riski Bunlar zaten sonlandırılan, çünkü sonlandırıcıyı kod yolunda sonlandırılabilir tüm nesnelere erişme.  
  
 Örneğin, başka bir sonlandırılabilir nesne B başvuruyor sonlandırılabilir bir nesne A güvenilir bir şekilde B A'ın kullanamazsınız sonlandırıcıyı, veya tam tersi. Sonlandırıcılar (eksikliği kritik sonlandırma için zayıf bir sıralama garanti) rastgele sırayla denir.  
  
 Ayrıca, bir uygulama etki alanı kaldırma sırasında veya işlem sonlandırma sırasında bazı noktalarda statik değişkenler depolanan nesneler da toplanan olduğunu unutmayın. Sonlandırılabilir nesne (veya statik değişkenler depolanan değerleri kullanabilecek statik bir yöntemini çağırmadan) başvurduğu statik bir değişken olabilir erişme güvenli IF <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> true değerini döndürür.  
  
 **✓ YAPMAK** olun, `Finalize` korumalı yöntemi.  
  
 Çünkü bu kılavuz zorlamak için derleyicileri yardımcı C#, C++ ve VB.NET geliştiriciler bu hakkında endişelenmeniz gerekmez.  
  
 **X yok** let özel durumlar kaçış sistem kritik hataları dışında Sonlandırıcısı mantığı gelen.  
  
 Sonlandırıcı bir özel durum, CLR (itibariyle .NET Framework sürüm 2.0), tüm işlem kapatılır yürütme ve denetimli bir şekilde yayımlanan kaynakları diğer sonlandırıcılar engelleyen.  
  
 **✓ DÜŞÜNÜN** oluşturma ve kritik sonlandırılabilir nesnesini kullanarak (içeren bir tür hiyerarşisinde bir türüyle <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) içinde bir sonlandırıcı kesinlikle gerekir yürütme zorlanmış uygulama etki alanı kaldırır ve iş parçacığı karşısında bile durumlar için durdurur.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 [Framework tasarım yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Ortak tasarım desenleri](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 [Çöp toplama](../../../docs/standard/garbage-collection/index.md)
