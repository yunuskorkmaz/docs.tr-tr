---
title: COM Aranabilir Sarmalayıcısı
ms.date: 10/23/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CCW
- COM interop, COM wrappers
- COM wrappers
- callable wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: d04be3b5-27b9-4f5b-8469-a44149fabf78
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8e2cab36c1dd990a1bf848067e7ae81baeb9ed8
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355057"
---
# <a name="com-callable-wrapper"></a>COM Aranabilir Sarmalayıcısı

Bir COM istemcisi bir .NET nesnesini çağırdığında, ortak dil çalışma zamanı yönetilen nesneyi ve nesne için bir COM çağrılabilir sarmalayıcı (CCW) oluşturur. Başvuru bir .NET nesnesini doğrudan COM istemcileri CCW bir proxy olarak yönetilen bir nesne için kullanın.

Çalışma zamanı hizmetlerinin isteyen COM istemcileri sayısından bağımsız olarak yönetilen bir nesne için tam olarak bir saat oluşturur. Aşağıdaki çizimde gösterildiği gibi birden çok COM istemcileri INew arabirimi kullanıma sunan CCW başvuru barındırabilir. CCW sırayla arabirimi uygulayan yönetilen bir nesne için tek bir başvuru içerir ve atık olarak toplanmış. COM hem .NET istemcileri, istekleri için aynı anda aynı yönetilen nesne üzerinde hale getirebilirsiniz.

![COM çağrılabilir sarmalayıcısı](./media/ccw.gif "ccw") COM çağrılabilir sarmalayıcı aracılığıyla erişme .NET nesneleri

COM aranabilir sarmalayıcılar, .NET Framework içinde çalışan diğer sınıflar için görünmez. Birincil amaçları, yönetilen ve yönetilmeyen kod arasındaki çağrıların sıralamanız sağlamaktır; Ancak, CCWs nesne kimliğini ve nesne yaşam süresi bunlar kaydırma yönetilen nesnelerin yönetin.

## <a name="object-identity"></a>Nesne Kimliği

Çalışma zamanı, nesne bellekte gerektiği gibi hareket etmek çalışma zamanı sağlayan kendi atık olarak toplanmış yığınla, gelen .NET nesne için bellek ayırır. Buna karşılık, çalışma zamanı sarmalayıcı doğrudan başvurmak COM istemcileri için çözmelerine noncollected yığın, gelen CCW için bellek ayırır.

## <a name="object-lifetime"></a>Nesne ömrü

.NET istemci sarmaladığı CCW başvuru-geleneksel COM biçiminde sayılır. Sarmalayıcı CCW başvuru sayısını sıfır ulaştığında, yönetilen nesne üzerinde onun başvuru serbest bırakır. Kalan başvuru ile yönetilen bir nesnenin sonraki çöp toplama döngüsü sırasında toplanır.

## <a name="simulating-com-interfaces"></a>COM arabirimlerinin benzetimi

SAAT, tüm genel, COM görünebilir arabirimler, veri türleri ve dönüş değerleri ile etkileşim arabirimi tabanlı COM'ın zorlama tutarlı bir şekilde COM istemcilerine kullanıma sunar. Bir COM istemcisi için bir .NET Framework nesnesi yöntemleri çağrılırken bir COM nesnesi üzerinde yöntemleri çağırmak için aynıdır.

Bu sorunsuz yaklaşım oluşturmak için CCW geleneksel COM arabirimleri gibi üreten **IUnknown** ve **IDispatch**. Aşağıdaki çizimde gösterildiği gibi saatin tersi YÖNDE sarmaladığı .NET nesne üzerinde tek bir başvuru tutar. COM istemcisi ve .NET nesne CCW. proxy ve saplama yapımı birbiriyle etkileşim

![COM arabirimleri](./media/ccwwithinterfaces.gif "ccwwithinterfaces") COM arabirimlerinde ve COM çağrılabilir sarmalayıcısı

Açıkça yönetilen bir ortamda bir sınıf tarafından uygulanan arabirimler gösterme ek olarak, .NET Framework uygulamaları nesne adına aşağıdaki tabloda listelenen COM arabirimleri sağlar. Bir .NET sınıf kendi uygulaması bu arabirimlerin sağlayarak varsayılan davranışı geçersiz kılabilirsiniz. Ancak, çalışma zamanının uygulamasını her zaman sağlar **IUnknown** ve **IDispatch** arabirimleri.

|Arabirim|Açıklama|
|---------------|-----------------|
|**IDispatch**|Geç bağlama türü bir mekanizma sağlar.|
|**IErrorInfo**|Hata, kaynağı, bir Yardım dosyası, Yardım bağlamı ve hata tanımlı arabiriminin GUID'si değerinin metinsel bir açıklaması verilmiştir (her zaman **GUID_NULL** .NET sınıfları için).|
|**IProvideClassInfo**|Erişim elde etmek COM istemcileri etkinleştirir **ITypeInfo** yönetilen bir sınıf tarafından uygulanan arabirimi.|
|**ISupportErrorInfo**|Yönetilen Nesne destekleyip desteklemediğini belirlemek üzere bir COM istemcisi sağlayan **IErrorInfo** arabirimi. Bu durumda, istemcinin en son özel durum nesnesine bir işaretçi alma sağlar. Tüm yönetilen türleri desteği **IErrorInfo** arabirimi.|
|**ITypeInfo**|Tlbexp.exe tarafından üretilen tür bilgilerini tam olarak aynıdır bir sınıf için tür bilgisini sağlar.|
|**IUnknown**|Standart uygulamasını sağlar **IUnknown** arabirimi hangi COM istemcisi CCW ömrünü yönetir ve türü zorlama sağlar.|

 Yönetilen bir sınıf ayrıca aşağıdaki tabloda açıklanan COM arabirimleri sağlar.

|Arabirim|Açıklama|
|---------------|-----------------|
|(\_*Classname*) sınıf arabirimi|Çalışma zamanı tarafından kullanıma sunulan ve açıkça tanımlanmış, arabirim, tüm ortak arabirimler, yöntemler, özellikler ve yönetilen bir nesne üzerinde açıkça gösterilen alanlar kullanıma sunar.|
|**IConnectionPoint** ve **IConnectionPointContainer**|Temsilci tabanlı olay (etkinlik abonelerinden kaydetmek için bir arabirimi) kaynak nesneleri için arabirim.|
|**Idispatchex**|Arabirim sınıfı kullanılıyorsa çalışma zamanı tarafından sağlanan **IExpando**. **Idispatchex** arabirimi uzantısıdır **IDispatch** aksine, arabirim **IDispatch**, numaralandırma, ekleme, silme, sağlar ve büyük/küçük harfe üyeleri çağırma.|
|**IEnumVARIANT**|Arabirim için koleksiyon türü sınıflar, sınıf uyguluyorsa, koleksiyondaki nesneleri numaralandırır **IEnumerable**.|

## <a name="introducing-the-class-interface"></a>Sınıf arabirimine giriş

Açıkça yönetilen kodda tanımlı değil, sınıf arabirimi tüm genel yöntemler, özellikler, alanlar ve .NET nesne üzerinde açık olayları ortaya koyan bir arabirimdir. Bu arabirim, bir çift veya yalnızca gönderme arabirimi olabilir. Sınıf arabirimine bir alt çizgi öncesinde .NET sınıfın kendisi adını alır. Örneğin, sınıf Mammal sınıfı arabirimidir \_Mammal.

Türetilen sınıflar için sınıf arabirimi tüm genel yöntemler, özellikler ve alanları temel sınıfın sunar. Türetilmiş sınıf ayrıca her bir temel sınıf için bir sınıf arabirimi kullanıma sunar. Örneğin, sınıf Mammal sınıfı MammalSuperclass geçerse, kendisi System.Object genişletir, COM istemcilerinin .NET nesne çıkarır üç adlı arabirimleri sınıf \_Mammal, \_MammalSuperclass, ve \_nesne.

Örneğin, aşağıdaki .NET sınıf göz önünde bulundurun:

```vb
' Applies the ClassInterfaceAttribute to set the interface to dual.
<ClassInterface(ClassInterfaceType.AutoDual)> _
' Implicitly extends System.Object.
Public Class Mammal
    Sub Eat()
    Sub Breathe()
    Sub Sleep()
End Class
```

```csharp
// Applies the ClassInterfaceAttribute to set the interface to dual.
[ClassInterface(ClassInterfaceType.AutoDual)]
// Implicitly extends System.Object.
public class Mammal
{
    public void Eat() {}
    public void Breathe() {}
    public void Sleep() {}
}
```

COM istemcisi adlı bir sınıf arabirimi için bir işaretçi edinebilirsiniz `_Mammal`, Tür Kitaplığı'nda açıklanan, [tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) aracı oluşturur. Varsa `Mammal` sınıfı bir veya daha fazla arabirim uygulandı, arabirimler coclass'ı altında görünür.

```
[odl, uuid(…), hidden, dual, nonextensible, oleautomation]
interface _Mammal : IDispatch
{
    [id(0x00000000), propget] HRESULT ToString([out, retval] BSTR*
        pRetVal);
    [id(0x60020001)] HRESULT Equals([in] VARIANT obj, [out, retval]
        VARIANT_BOOL* pRetVal);
    [id(0x60020002)] HRESULT GetHashCode([out, retval] short* pRetVal);
    [id(0x60020003)] HRESULT GetType([out, retval] _Type** pRetVal);
    [id(0x6002000d)] HRESULT Eat();
    [id(0x6002000e)] HRESULT Breathe();
    [id(0x6002000f)] HRESULT Sleep();
}
[uuid(…)]
coclass Mammal
{
    [default] interface _Mammal;
}
```

Sınıf arabirimi oluşturma isteğe bağlıdır. Varsayılan olarak, COM birlikte çalışma için bir tür kitaplığı dışarı her sınıf için bir salt arabirimi oluşturur. Engelleyebilir veya uygulayarak bu arabirimi otomatik olarak oluşturulmasını değiştirme <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> sınıfınıza. Sınıf arabirimi yönetilen sınıflar com'da gösterme görevini kolaylaştırabilir olsa da, kullanımları sınırlıdır.

> [!CAUTION]
> Sınıf arabirimi kullanarak açıkça kendi tanımlamak yerine yönetilen sınıfınızın gelecekteki sürüm karmaşık hale getirebilir. Sınıf arabirimi kullanmadan önce lütfen aşağıdaki yönergeleri okuyun.

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a>COM istemcilerine sınıf arabirimi oluşturmak yerine kullanmak için açık bir arabirim tanımlayın.

COM birlikte çalışma sınıf arabirimi otomatik olarak oluşturduğundan, sınıfınıza sonrası sürüm değişikliklerini ortak dil çalışma zamanı tarafından kullanıma sunulan sınıf arabirimi düzenini değiştirebilirsiniz. COM istemcileri bir arabirimin düzen değişiklikleri işlemek genellikle hazırlıksız olduğundan, bunlar sınıf üye yerleşimini değiştirirseniz bölün.

Bu kılavuz arabirimler COM istemcilerine maruz değiştirilemez kalması gereken kavram çalışacak şekilde güçlendirir. COM istemcileri arabirimi düzenini yanlışlıkla yeniden sıralayarak bozucu riskini azaltmak için tüm değişiklikleri açıkça arabirimleri tanımlayarak sınıfa arabirimi düzenden yalıtın.

Kullanım **ClassInterfaceAttribute** sınıf arabirimi otomatik olarak oluşturulmasını disengage ve aşağıdaki kod parçasını gösterildiği gibi sınıfın açık bir arabirim uygulamak için:

```vb
<ClassInterface(ClassInterfaceType.None)>Public Class LoanApp
    Implements IExplicit
    Sub M() Implements IExplicit.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.None)]
public class LoanApp : IExplicit
{
    int IExplicit.M() { return 0; }
}
```

**ClassInterfaceType.None** değer sınıfı meta veriler için bir tür kitaplığı dışarı aktarılırken oluşturulan sınıf arabirimi engeller. Önceki örnekte, COM istemcileri erişebilir `LoanApp` aracılığıyla yalnızca sınıf `IExplicit` arabirimi.

### <a name="avoid-caching-dispatch-identifiers-dispids"></a>Gönderme tanımlayıcıları (DISPID değeri) önbelleğe alma kaçının

Sınıf arabirimi kullanarak, betikleştirilmiş istemcileri, Microsoft Visual Basic 6.0 istemciler veya arabirim üyelerinin DISPID değeri önbelleğe alma herhangi bir geç bağlanan istemci için kabul edilebilir bir seçenektir. DISPID değeri geç bağlama etkinleştirmek için arabirim üyeleri tanımlar.

Sınıf arabirimi için nesil DISPID değeri arabirimin üyesi konumunu temel alır. Üye sırasını değiştirmek ve sınıfı bir tür kitaplığına aktardığınızdan, sınıf arabirimi içinde oluşturulan DISPID değeri değiştirir.

Sınıf arabirimi kullanılırken geç bağlanan COM istemcilerini bozmayı önlemek için uygulama **ClassInterfaceAttribute** ile **ClassInterfaceType.AutoDispatch** değeri. Bu değer yalnızca gönderme sınıf arabirimi uygular, ancak arabirim açıklaması tür kitaplığındaki atlar. Bir arabirim açıklaması istemciler DISPID değeri, derleme zamanı önbelleğine erişemiyor. Bu sınıf arabirimi için varsayılan arabirim türü olsa da, öznitelik değeri açıkça uygulayabilirsiniz.

```vb
<ClassInterface(ClassInterfaceType.AutoDispatch)> Public Class LoanApp
    Implements IAnother
    Sub M() Implements IAnother.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.AutoDispatch)]
public class LoanApp
{
    public int M() { return 0; }
}
```

DISPID arabirim üyesini çalışma zamanında almak için COM istemcileri çağırabilirsiniz **IDispatch.GetIdsOfNames**. Arabirimdeki bir yöntem çağırmak için bir bağımsız değişken olarak döndürülen DispId geçirmek **IDispatch.Invoke**.

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a>Sınıf arabirimi için çift arabirim seçeneğini kullanarak kısıtlayın.

Çift arabirimler COM istemcileri tarafından arabirim üyeleri erken ve geç bağlama etkinleştirin. Tasarım zamanında ve test sırasında sınıf arabirimi için çift ayarlamak yararlı olabilir. Yönetilen bir sınıf (ve temel sınıfları) hiçbir zaman olacak değiştirilmiş, bu da kabul edilebilir bir seçenektir. Diğer tüm durumlarda, sınıf arabirimi çift ayarlamaktan kaçının.

Otomatik olarak oluşturulan bir çift arabirim nadir durumlarda uygun olabilir; Ancak, daha sık bu sürümü ile ilgili karmaşıklığı oluşturur. Örneğin, türetilmiş bir sınıfın sınıf arabirimi kullanarak COM istemcilerinde değişikliklerle kolayca temel sınıfa bozabilir. Bir üçüncü taraf taban sınıfı sağlar, sınıf arabirimi düzenini denetiminiz dışında değildir. Daha fazla, yalnızca gönderme arabirimi çift arabirim (**ClassInterfaceType.AutoDual**) sınıf arabirimi dışarı aktarılan Tür Kitaplığı'nda bir açıklaması verilmiştir. Böyle bir açıklamasını, çalışma zamanında önbelleğe DISPID değeri geç bağlanan istemciler teşvik eder.

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a>Tüm COM olay bildirimleri geç bağlanan olduğundan emin olun.

Varsayılan olarak, COM tür bilgilerini doğrudan yönetilen derlemelere, birincil birlikte çalışma derlemeleri (PIA) gereksinimini ortadan kaldırır katıştırılır. Ancak, gömülü tür bilgileri sınırlamaları, vtable erken bağlanan çağrılar tarafından COM olay bildirimleri teslim desteklenmiyor ancak yalnızca geç bağlanan destekler biridir `IDispatch::Invoke` çağırır.

Uygulamanıza erken bağlanan çağrılar COM olay arabirim yöntemleri için gerekiyorsa ayarlayabileceğiniz **birlikte çalışma türlerini katıştır** özelliği için Visual Studio'da `true`, veya proje dosyanızda aşağıdaki öğeyi ekleyin:

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [COM Sarmalayıcıları](com-wrappers.md)
- [.NET Framework Bileşenlerini COM'da Gösterme](exposing-dotnet-components-to-com.md)
- [Birlikte Çalışma için .NET Türlerini Niteleme](qualifying-net-types-for-interoperation.md)
- [Çalışma Zamanında Çağrılabilir Sarmalayıcı](runtime-callable-wrapper.md)
