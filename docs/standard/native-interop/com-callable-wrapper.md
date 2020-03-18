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
ms.openlocfilehash: 6f2f4055a95dbcea8d7872b5c5fa3ccede8c2c8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400381"
---
# <a name="com-callable-wrapper"></a>COM Aranabilir Sarmalayıcısı

Bir COM istemcisi bir .NET nesnesi aradığında, ortak dil çalışma süresi yönetilen nesneyi ve nesne için com çağrılabilir sarıcı (CCW) oluşturur. Bir .NET nesnesine doğrudan başvuruyapamayan COM istemcileri, yönetilen nesne için CCW'yi proxy olarak kullanır.

Çalışma süresi, hizmetlerini isteyen COM istemcilerinin sayısına bakılmaksızın yönetilen bir nesne için tam olarak bir CCW oluşturur. Aşağıdaki resimde de görüldüğü gibi, birden çok COM istemcisi, INew arabirimini ortaya çıkaran CCW'ye bir başvuru tutabilir. CCW, sırayla, arabirimi uygulayan yönetilen nesneye tek bir başvuru tutar ve toplanan çöp. Hem COM hem de .NET istemcileri aynı yönetilen nesne üzerinde aynı anda istekte bulunabilir.

![INew'ı ortaya çıkaran CCW'ye referans tutan birden çok COM istemcisi.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

COM çağrılabilir sarmalayıcılar .NET çalışma süresi içinde çalışan diğer sınıflar için görünmez. Birincil amaçları yönetilen ve yönetilmeyen kod arasındaki aramaları mareşal etmektir; ancak, CCW'ler de sardıkları yönetilen nesnelerin nesne kimliğini ve nesne yaşam ömrünü yönetir.

## <a name="object-identity"></a>Nesne Kimliği

Çalışma zamanı, .NET nesnesi için bellek ayırır ve çalışma zamanının nesneyi gerektiği gibi bellekte hareket ettirmesini sağlar. Buna karşılık, çalışma süresi, CCW için toplanan olmayan bir yığından bellek ayırır ve COM istemcilerinin sarıcıya doğrudan başvurmasını mümkün kılar.

## <a name="object-lifetime"></a>Nesne Yaşam Süresi

Sarar .NET istemcisinin aksine, CCW geleneksel COM modasında referans sayılır. CCW'deki başvuru sayısı sıfıra ulaştığında, sarıcı başvuruyu yönetilen nesne üzerinde serbest bırakır. Sonraki çöp toplama döngüsü sırasında, kalan başvuruları olmayan yönetilen bir nesne toplanır.

## <a name="simulating-com-interfaces"></a>COM arayüzlerini simüle etme

CCW, com istemcilerine tüm ortak, COM görünür arabirimleri, veri türleri ve döndürme değerlerini, COM'un arabirim tabanlı etkileşimuygulamasıyla tutarlı bir şekilde ortaya çıkarır. Bir COM istemcisi için,.NET nesnesi üzerinde yöntemleri çağırmak, COM nesnesindeki yöntemleri çağırmakla aynıdır.

Bu sorunsuz yaklaşımı oluşturmak için CCW, **IUnknown** ve **IDispatch**gibi geleneksel COM arabirimleri üretmektedir. Aşağıdaki resimde gösterildiği gibi, CCW sarar .NET nesnesi üzerinde tek bir başvuru tutar. Hem COM istemcisi hem de .NET nesnesi CCW'nin proxy ve saplama yapısı aracılığıyla birbirleriyle etkileşime geçer.

![CCW'nin COM arabirimlerini nasıl ürettiğini gösteren diyagram.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

Yönetilen ortamda bir sınıf tarafından açıkça uygulanan arabirimleri ortaya çıkarmanın yanı sıra, .NET çalışma zamanı nesne adına aşağıdaki tabloda listelenen COM arabirimlerinin uygulamalarını sağlar. Bir .NET sınıfı, bu arabirimlerin kendi uygulamasını sağlayarak varsayılan davranışı geçersiz kılabilir. Ancak, çalışma zamanı her zaman **IUnknown** ve **IDispatch** arabirimleri için uygulama sağlar.

|Arabirim|Açıklama|
|---------------|-----------------|
|**ıdispatch**|Türüne geç bağlama için bir mekanizma sağlar.|
|**ıerrorınfo**|Hatanın, kaynağının, Yardım dosyasının, Yardım bağlamının ve hatayı tanımlayan arabirimin GUID'sinin (her zaman .NET sınıfları için **GUID_NULL)** metinsel bir açıklamasını sağlar.|
|**IProvideClassInfo**|COM istemcilerinin yönetilen bir sınıf tarafından uygulanan **ITypeInfo** arabirimine erişmesini sağlar. COM'dan alınmayan türler için .NET Core'da döner. `COR_E_NOTSUPPORTED` |
|**ısupporterrorınfo**|Yönetilen nesnenin **IErrorInfo** arabirimini destekleyip desteklemediğini belirlemek için bir COM istemcisi sağlar. Bu nedenle, istemci nin en son özel durum nesnesine bir işaretçi almasını sağlar. Yönetilen tüm türler **IErrorInfo** arabirimini destekler.|
|**ITypeInfo** (Sadece.NET Framework)|Tlbexp.exe tarafından üretilen tür bilgileriyle tam olarak aynı olan bir sınıf için tür bilgileri sağlar.|
|**IUnknown**|COM istemcisinin CCW'nin ömrünü yönettiği ve tür zorlamasağladığı **IUnknown** arabiriminin standart uygulamasını sağlar.|

 Yönetilen bir sınıf, aşağıdaki tabloda açıklanan COM arabirimlerini de sağlayabilir.

|Arabirim|Açıklama|
|---------------|-----------------|
|(\_*Sınıf adı*) sınıf arabirimi|Yönetilen bir nesne üzerinde açıkça açıkta kalan tüm ortak arabirimleri, yöntemleri, özellikleri ve alanları ortaya çıkaran, çalışma zamanı tarafından açıkta kalan ve açıkça tanımlanmamış arabirim.|
|**IConnectionPoint** ve **IConnectionPointContainer**|Temsilci tabanlı olaylara kaynak sağlayan nesneler için arabirim (olay abonelerini kaydetmek için bir arabirim).|
|**IDispatchEx** (.NET Framework Only)|Sınıf **IExpando'yu**uyguluyorsa çalışma zamanı tarafından sağlanan arabirim. **IDispatchEx** arabirimi, **IDispatch'in**aksine, üyelerin numaralandırma, ekleme, silme ve büyük/küçük harf duyarlı aramalarına olanak tanıyan **IDispatch** arabiriminin bir uzantısıdır.|
|**ıenumvarıant**|Sınıf **Ayrılmaz**uygularsa koleksiyondaki nesneleri sayısalhale getiren koleksiyon türü sınıflar için arabirim.|

## <a name="introducing-the-class-interface"></a>Sınıf arabirimini tanıtma

Yönetilen kodda açıkça tanımlanmayan sınıf arabirimi, .NET nesnesinde açıkça açık tabir edilen tüm ortak yöntemleri, özellikleri, alanları ve olayları ortaya çıkaran bir arabirimdir. Bu arabirim, yalnızca çift veya yalnızca göndere gönderilen bir arabirim olabilir. Sınıf arabirimi, bir alt alt skorun öncesinde .NET sınıfının adını alır. Örneğin, sınıf Memeliler için sınıf \_arabirimi Memeli'dir.

Türemiş sınıflar için sınıf arabirimi, taban sınıfın tüm ortak yöntemlerini, özelliklerini ve alanlarını da gösterir. Türetilen sınıf, her taban sınıf için bir sınıf arabirimi de ortaya çıkarır. Örneğin, sınıf Memeli sinifini genişletirse, kendisi System.Object' i genişletir, .NET \_nesnesi COM istemcilerine Memeli, \_MemeliSuperclass ve \_Nesne adlIkiüç sınıf arabirimini gösterir.

Örneğin, aşağıdaki .NET sınıfını göz önünde bulundurun:

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

COM istemcisi adlı `_Mammal`bir sınıf arabirimi için bir işaretçi elde edebilirsiniz. .NET Framework'de, arayüz tanımını içeren bir tür kitaplığı oluşturmak için Tür `_Mammal` [Kitaplığı İhracatçısı (Tlbexp.exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) aracını kullanabilirsiniz. Tip Kitaplığı İhracatçısı .NET Core'da desteklenmez. `Mammal` Sınıf bir veya daha fazla arabirim uyguladıysa, arabirimler ortak sınıfın altında görünür.

```console
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

Sınıf arabiriminin oluşturması isteğe bağlıdır. Varsayılan olarak, COM interop bir tür kitaplığı için dışa aktardığınız her sınıf için yalnızca gönderme arabirimi oluşturur. Sınıfınıza uygulayarak <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> bu arabirimin otomatik oluşturulmasını engelleyebilir veya değiştirebilirsiniz. Sınıf arabirimi yönetilen sınıfları COM'a maruz bırakma görevini kolaylaştırsa da, kullanımları sınırlıdır.

> [!CAUTION]
> Sınıf arabirimini kullanmak, kendi sınıfınızı açıkça tanımlamak yerine yönetilen sınıfınuzun gelecekteki sürümünü zorlaştırabilir. Sınıf arabirimini kullanmadan önce lütfen aşağıdaki yönergeleri okuyun.

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a>Sınıf arabirimi oluşturmak yerine COM istemcilerinin kullanması için açık bir arabirim tanımlayın.

COM interop otomatik olarak bir sınıf arabirimi oluşturduğundan, sınıfınızdaki sürüm sonrası değişiklikler, ortak dil çalışma zamanı tarafından açığa çıkarılan sınıf arabiriminin düzenini değiştirebilir. COM istemcileri genellikle arabirimin düzenindeki değişiklikleri işlemek için hazır olmadığından, sınıfın üye düzenini değiştirirseniz kırılırlar.

Bu kılavuz, COM istemcilerine maruz kalan arabirimlerin değiştirilemez kalması gerektiği fikrini güçlendirmektedir. Arabirim düzenini yanlışlıkla yeniden sıralayarak COM istemcilerini kırma riskini azaltmak için, arabirimleri açıkça tanımlayarak sınıfdaki tüm değişiklikleri arabirim düzeninden yalıtın.

Sınıf arabiriminin otomatik neslini devre dışı bırakıp, aşağıdaki kod parçasının gösterdiği gibi sınıf için açık bir arabirim uygulamak için **ClassInterfaceAtöz'ü** kullanın:

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

**ClassInterfaceType.None** değeri, sınıf meta verileri bir tür kitaplığına dışa aktarıldığında sınıf arabiriminin oluşturulmasını engeller. Önceki örnekte, COM istemcileri `LoanApp` sınıfa yalnızca `IExplicit` arabirim üzerinden erişebilir.

### <a name="avoid-caching-dispatch-identifiers-dispids"></a>Sevk tanımlayıcılarını (DispIds) önbelleğe almaktan kaçının

Sınıf arabirimini kullanmak, komut dosyası istemcileri, Microsoft Visual Basic 6.0 istemcileri veya arabirim üyelerinin DispId'lerini önbelleğe alamayan herhangi bir geç bağlantı istemcisi için kabul edilebilir bir seçenektir. DispIds geç bağlama sağlamak için arabirim üyelerini tanımlar.

Sınıf arabirimi için, DispIds oluşturma arabirimde üyenin konumuna dayanır. Üyenin sırasını değiştirir ve sınıfı bir tür kitaplığına dışa aktarırsanız, sınıf arabiriminde oluşturulan DispId'leri değiştirirsiniz.

Sınıf arabirimini kullanırken geç bağlanan COM istemcilerini kırmamak için **ClassInterfaceType.AutoDispatch** değeriyle **ClassInterfaceAttribute** uygulayın. Bu değer yalnızca gönderilen sınıf arabirimi uygular, ancak tür kitaplığından arabirim açıklamasını atlar. Arabirim açıklaması olmadan, istemciler Derleme zamanında DispId'leri önbelleğe alamıyor. Bu sınıf arabirimi için varsayılan arabirim türü olsa da, öznitelik değerini açıkça uygulayabilirsiniz.

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

Çalışma zamanında bir arayüz üyesinin DispId almak için, COM **istemcileri IDispatch.GetIdsOfNames**arayabilirsiniz. Arabirimde bir yöntem çağırmak için, döndürülen DispId'i bağımsız değişken olarak **IDispatch.Invoke'a geçirin.**

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a>Sınıf arabirimi için çift arabirim seçeneğini kullanarak kısıtlayın.

Çift arabirimler, COM istemcileri tarafından arayüz üyelerine erken ve geç bağlanmayı sağlar. Tasarım zamanında ve sınama sırasında, sınıf arabirimini çift olarak ayarlamayı yararlı bulabilirsiniz. Hiçbir zaman değiştirilmeyecek yönetilen bir sınıf (ve temel sınıfları) için bu seçenek de kabul edilebilir. Diğer tüm durumlarda, sınıf arabirimini çift olarak ayarlamaktan kaçının.

Otomatik olarak oluşturulan çift arabirim nadir durumlarda uygun olabilir; ancak, daha sık sürümle ilgili karmaşıklık oluşturur. Örneğin, türetilmiş bir sınıfın sınıf arabirimini kullanan COM istemcileri taban sınıfdeğişiklikleriyle kolayca kırılabilir. Üçüncü bir taraf taban sınıfı sağladığında, sınıf arabiriminin düzeni sizin denetiminiz dışındadır. Ayrıca, yalnızca gönderilen bir arabirimin aksine, çift arabirim **(ClassInterfaceType.AutoDual)** dışa aktarılan tür kitaplığında sınıf arabiriminin açıklamasını sağlar. Böyle bir açıklama, geç giden istemcileri derleme zamanında DispId'leri önbelleğe almaya teşvik eder.

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a>Tüm COM olay bildirimlerinin geç olduğundan emin olun.

Varsayılan olarak, COM türü bilgileri doğrudan yönetilen derlemelere gömülür ve bu da birincil interop derlemeleri (PI'ler) gereksinimini ortadan kaldırır. Ancak, katıştırılmış tür bilgilerinin sınırlamalarından biri, COM olay bildirimlerinin erken bağlanan vtable çağrıları `IDispatch::Invoke` tarafından teslimini desteklememesi, yalnızca geç gelen çağrıları desteklemesidir.

Uygulamanız COM olay arabirimi yöntemlerine erken çağrı gerektiriyorsa, Visual Studio'daki `true` **Embed Interop Types** özelliğini Visual Studio'da ayarlayabilir veya proje dosyanıza aşağıdaki öğeyi ekleyebilirsiniz:

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [COM Sarmalayıcıları](com-wrappers.md)
- [.NET Framework Bileşenlerini COM'da Gösterme](../../framework/interop/exposing-dotnet-components-to-com.md)
- [.NET Core Bileşenlerini COM’da Gösterme](../../core/native-interop/expose-components-to-com.md)
- [Birlikte Çalışma için Niteleyici .NET Türleri](qualify-net-types-for-interoperation.md)
- [Çalışma Zamanı Aranabilir Sarmalayıcısı](runtime-callable-wrapper.md)
