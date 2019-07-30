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
ms.openlocfilehash: 601f9a216bc2e11ccb34f1f3b3df267002efb01f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631335"
---
# <a name="com-callable-wrapper"></a>COM Aranabilir Sarmalayıcısı

Bir COM istemcisi .NET nesnesini çağırdığında, ortak dil çalışma zamanı, yönetilen nesneyi ve nesne için COM çağrılabilir sarmalayıcı (CCW) oluşturur. Doğrudan bir .NET nesnesine başvuru yapılamıyor COM istemcileri, yönetilen nesne için bir proxy olarak CCW kullanır.

Çalışma zamanı, kendi hizmetlerini isteyen COM istemcilerinin sayısından bağımsız olarak, yönetilen bir nesne için tam olarak bir CCW oluşturur. Aşağıdaki çizimde gösterildiği gibi, birden fazla COM istemcisi, INew arabirimini kullanıma sunan CCW bir başvuru tutabilir. CCW, sırasıyla, arabirimini uygulayan ve atık olarak toplanan yönetilen nesneye tek bir başvuru içerir. Hem COM hem de .NET istemcileri aynı yönetilen nesne üzerinde aynı anda istek yapabilir.

![INew 'yi ortaya çıkaran CCW başvurusunu tutan birden fazla COM istemcisi.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

COM çağrılabilir sarmalayıcılar, .NET çalışma zamanı içinde çalışan diğer sınıfların görünmez hale gelir. Birincil amacı yönetilen ve yönetilmeyen kod arasındaki çağrıları sıralayamaz; Ancak CCWs, sardıkları yönetilen nesnelerin nesne kimliğini ve nesne ömrünü de yönetebilir.

## <a name="object-identity"></a>Nesne Kimliği

Çalışma zamanı, bir .NET nesnesi için bellek ayırır ve bu, çalışma zamanının nesneyi gerektiği şekilde belleğin etrafında taşımasına olanak sağlar. Buna karşılık, çalışma zamanı, toplanan bir yığından CCW için bellek ayırır ve COM istemcilerinin doğrudan sarmalayıcı 'a başvurmasına olanak tanır.

## <a name="object-lifetime"></a>Nesne ömrü

Sarmaladığı .NET istemcisinin aksine, CCW başvurusu geleneksel COM olarak sayılır. CCW üzerindeki başvuru sayısı sıfıra ulaştığında, sarmalayıcı yönetilen nesne üzerinde başvurusunu serbest bırakır. Sonraki atık toplama çevrimi sırasında kalan başvuruları olmayan yönetilen bir nesne toplanır.

## <a name="simulating-com-interfaces"></a>COM arabirimlerinin benzetimi yapma

CCW tüm genel, COM görünebilir arabirimleri, veri türlerini ve dönüş değerlerini com istemcilerine COM 'un arabirim tabanlı etkileşim zorlaması ile tutarlı bir şekilde sunar. Bir COM istemcisi için, bir .NET nesnesi üzerinde Yöntemler çağırma bir COM nesnesi üzerinde Yöntemler çağırma ile aynıdır.

Bu sorunsuz yaklaşımı oluşturmak için CCW, **IUnknown** ve **ıDISPATCH**gibi geleneksel com arabirimleri oluşturur. Aşağıdaki çizimde gösterildiği gibi CCW, sarmaladığı .NET nesnesinde tek bir başvuru tutar. Hem COM istemcisi hem de .NET nesnesi, CCW için proxy ve saplama oluşturma aracılığıyla birbirleriyle etkileşime geçer.

![CCW 'in COM arabirimlerini nasıl kullandığını gösteren diyagram.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

.NET çalışma zamanı, yönetilen ortamdaki bir sınıf tarafından açıkça uygulanan arabirimleri açığa çıkarmasına ek olarak, nesne adına aşağıdaki tabloda listelenen COM arabirimlerinin uygulamalarını sağlar. .NET sınıfı, bu arabirimlerin kendi uygulamasını sağlayarak varsayılan davranışı geçersiz kılabilir. Ancak çalışma zamanı her zaman **IUnknown** ve **IDispatch** arabirimlerinin uygulamasını sağlar.

|Arabirim|Açıklama|
|---------------|-----------------|
|**IDispatch**|Türe geç bağlama için bir mekanizma sağlar.|
|**IErrorInfo**|Hatanın metinsel bir açıklamasını, kaynağını, bir yardım dosyasını, yardım bağlamını ve hatayı tanımlayan arabirimin GUID 'sini (her zaman .NET sınıfları için **GUID_NULL** ) sağlar.|
|**IProvideClassInfo**|COM istemcilerinin yönetilen bir sınıf tarafından uygulanan **ITypeInfo** arabirimine erişim sağlamasına olanak sağlar. COM `COR_E_NOTSUPPORTED` 'dan içeri aktarılmayan türler için .NET Core ' u döndürür. |
|**Iupporterrorınfo**|Bir COM istemcisinin, yönetilen nesnenin **IErrorInfo** arabirimini destekleyip desteklemediğini belirlemesine olanak sağlar. Bu durumda, istemcinin en son özel durum nesnesine bir işaretçi almasını sağlar. Tüm yönetilen türler **IErrorInfo** arabirimini destekler.|
|**ITypeInfo** (Yalnızca .NET Framework)|Tlbexp. exe tarafından üretilen tür bilgileriyle tam olarak aynı olan bir sınıf için tür bilgilerini sağlar.|
|**IUnknown**|, COM istemcisinin CCW ömrünü yönettiği ve tür zorlaması sağladığı **IUnknown** arabiriminin standart uygulamasını sağlar.|

 Yönetilen bir sınıf, aşağıdaki tabloda açıklanan COM arabirimlerini de sağlayabilir.

|Arabirim|Açıklama|
|---------------|-----------------|
|(\_*ClassName*) sınıf arabirimi|Çalışma zamanı tarafından sunulan ve açıkça tanımlanmamış, tüm genel arabirimleri, yöntemleri, özellikleri ve yönetilen bir nesne üzerinde açık olarak açık olan alanları sunan arabirim.|
|**Inewctionpoint** ve **IConnectionPointContainer**|Temsilci tabanlı Olaylar (Olay aboneleri kaydetmek için bir arabirim) olan nesneler için arabirim.|
|**IDispatchEx** (Yalnızca .NET Framework)|Sınıf IBir uygularsa çalışma zamanı tarafından sağlananarabirim. **IDispatchEx** arabirimi **IDispatch arabiriminin bir** uzantısıdır. Bu, **IDispatch**'in aksine numaralandırma, ekleme, silme ve büyük/küçük harf duyarlı üyelerin çağrılmasını mümkün değildir.|
|**IEnumVariant**|Sınıf **IEnumerable**uygularsa koleksiyondaki nesneleri numaralandırır koleksiyon türü sınıfları için arabirim.|

## <a name="introducing-the-class-interface"></a>Sınıf arabirimine giriş

Yönetilen kodda açıkça tanımlanmayan sınıf arabirimi, tüm ortak Yöntemler, özellikler, alanlar ve .NET nesnesi üzerinde açık olarak açık olan olayları kullanıma sunan bir arabirimdir. Bu arabirim, bir çift veya salt dağıtım arabirimi olabilir. Sınıf arabirimi, öncesinde bir alt çizgi gelen .NET sınıfının adını alır. Örneğin, Mammal sınıfı için sınıf arabirimi Mammal ' dir \_.

Türetilmiş sınıflar için, sınıf arabirimi de temel sınıfın tüm ortak yöntemlerini, özelliklerini ve alanlarını gösterir. Türetilmiş sınıf Ayrıca her temel sınıf için bir sınıf arabirimi sunar. Örneğin, Mammal sınıfı mammalsüper sınıfını genişleterek System. Object ' i genişletir. .net nesnesi, com istemcilerinin Mammal, \_ \_mammalsüper ve \_nesne adlı üç sınıf arabirimine sahip olduğunu gösterir.

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

COM istemcisi adlı `_Mammal`bir sınıf arabirimine bir işaretçi alabilir. .NET Framework, `_Mammal` arabirim tanımını içeren bir tür kitaplığı oluşturmak için [tür kitaplığı verme programı (Tlbexp. exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) aracını kullanabilirsiniz. Tür kitaplığı verme programı .NET Core 'da desteklenmez. `Mammal` Sınıf bir veya daha fazla arabirim uyguladıysanız, arabirimler coclass altında görünür.

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

Sınıf arabiriminin oluşturulması isteğe bağlıdır. Varsayılan olarak COM birlikte çalışması, bir tür kitaplığına verdiğiniz her sınıf için yalnızca bir dağıtım arabirimi oluşturur. Sınıfınıza uygulayarak <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> bu arabirimin otomatik olarak oluşturulmasını engelleyebilir veya değiştirebilirsiniz. Sınıf arabirimi yönetilen sınıfları COM 'a gösterme görevini kolaylaştırabilir, ancak kullanımları sınırlıdır.

> [!CAUTION]
> Kendi kendinizinkini açıkça tanımlamak yerine sınıf arabirimini kullanarak, yönetilen sınıfınızın gelecek sürümü oluşturma sürecini karmaşıklaştırabilirsiniz. Sınıf arabirimini kullanmadan önce lütfen aşağıdaki yönergeleri okuyun.

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a>COM istemcilerinin sınıf arabirimini oluşturmak yerine kullanması için açık bir arabirim tanımlayın.

COM birlikte çalışması otomatik olarak bir sınıf arabirimi oluşturduğundan, sınıfınıza sürüm sonrası değişiklikler ortak dil çalışma zamanı tarafından sunulan sınıf arabiriminin yerleşimini değiştirebilir. COM istemcileri, bir arabirimin düzeninde değişiklikleri işlemeye yönelik olarak hazırlanmamış olduğundan, sınıfın üye yerleşimini değiştirirseniz bunlar kesilir.

Bu kılavuz, COM istemcilerine sunulan arabirimlerin değiştirilemeyen şekilde kalmasını sağlar. Arabirim yerleşimini yanlışlıkla yeniden sıralayarak COM istemcilerinin bölünmesi riskini azaltmak için, arabirimleri açıkça tanımlayarak arabirim düzeninden sınıftaki tüm değişiklikleri yalıtın.

Sınıf arabiriminin otomatik olarak oluşturulmasını ve aşağıdaki kod parçasının gösterdiği gibi sınıf için açık bir arabirim uygulamayı sağlamak için **ClassInterfaceAttribute** kullanın:

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

**ClassInterfaceType. None** değeri, sınıf meta verileri bir tür kitaplığına aktarıldığında sınıf arabiriminin oluşturulmasını engeller. Yukarıdaki örnekte, com istemcileri `LoanApp` sınıfına yalnızca `IExplicit` arabirim aracılığıyla erişebilir.

### <a name="avoid-caching-dispatch-identifiers-dispids"></a>Dağıtım tanımlayıcılarını (dispIDs) önbelleğe almayı önleyin

Sınıf arabirimini kullanmak, komut dosyalı istemciler, Microsoft Visual Basic 6,0 istemcileri veya arabirim üyelerinin Depıd 'leri önbelleğe Mayan herhangi bir geç bağlanan istemci için kabul edilebilir bir seçenektir. DispIDs, geç bağlamayı etkinleştirmek için arabirim üyelerini belirler.

Sınıf arabirimi için, dispIDs oluşturma işlemi, arabirimindeki üyenin konumunu temel alır. Üyenin sırasını değiştirir ve sınıfı bir tür kitaplığına dışarı aktardığınızda, sınıf arabiriminde oluşturulan dispID 'leri değiştirirsiniz.

Sınıf arabirimini kullanırken, geç bağlantılı COM istemcilerinin kesilmesini önlemek için classınterfacbir **. oto dağıtım** değeri Ile **ClassInterfaceAttribute** uygulayın. Bu değer yalnızca bir dağıtım sınıfı arabirimini uygular, ancak tür kitaplığından arabirim açıklamasını atlar. Arabirim açıklaması olmadan istemciler, derleme zamanında dispID 'leri önbelleğe alamıyor. Bu, sınıf arabirimi için varsayılan arabirim türü olsa da, öznitelik değerini açık bir şekilde uygulayabilirsiniz.

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

Çalışma zamanında bir arabirim üyesinin DISPID 'sini almak için, COM istemcileri **IDispatch. GetIDsOfNames**' i çağırabilir. Arabirimdeki bir yöntemi çağırmak için, döndürülen DISPID 'yi **IDispatch. Invoke**öğesine bir bağımsız değişken olarak geçirin.

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a>Sınıf arabirimi için Dual Interface seçeneğini kullanarak kısıtlayın.

Çift arabirimler, COM istemcilerine göre arabirim üyelerine erken ve geç bağlamayı etkinleştirir. Tasarım zamanında ve test sırasında, sınıf arabirimini çift olarak ayarlamayı yararlı bulabilirsiniz. Hiçbir değişiklik olmayacak yönetilen bir sınıf (ve temel sınıfları) için, bu seçenek de kabul edilebilir. Diğer tüm durumlarda, sınıf arabirimini çift olarak ayarlamaktan kaçının.

Otomatik olarak oluşturulan bir çift arabirim ender durumlarda uygun olabilir; Ancak, daha sık, sürümle ilgili karmaşıklık oluşturur. Örneğin, türetilmiş bir sınıfın sınıf arabirimini kullanan COM istemcileri, temel sınıftaki değişikliklerle kolayca kesilebilir. Üçüncü bir taraf temel sınıfı sağlıyorsa, sınıf arabiriminin düzeni denetimiden oluşur. Ayrıca, yalnızca bir dağıtım arabiriminden farklı olarak, bir çift arabirim (**ClassInterfaceType. oto Dual**), içe aktarılmış tür kitaplığındaki sınıf arabiriminin bir açıklamasını sağlar. Bu tür bir açıklama, geç bağlantılı istemcileri derleme zamanında dispID 'leri önbelleğe almak üzere önerir.

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a>Tüm COM olay bildirimlerinin geç bağlandığına emin olun.

Varsayılan olarak, COM tür bilgileri doğrudan yönetilen derlemelere katıştırılır ve bu da birincil birlikte çalışma derlemeleri (PIA 'lar) gereksinimini ortadan kaldırır. Ancak, gömülü tür bilgisinin kısıtlamalarından biri, com olay bildirimlerinin erken bağlanan vtable çağrılarına teslimini desteklemediğine karşın yalnızca geç bağlanan `IDispatch::Invoke` çağrıları destekler.

Uygulamanız com olay arabirimi yöntemlerine erken bağlantılı çağrılar gerektiriyorsa, Visual Studio 'daki **birlikte çalışma türlerini katıştır** özelliğini olarak `true`ayarlayabilir veya aşağıdaki öğeyi proje dosyanıza dahil edebilirsiniz:

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [COM Sarmalayıcıları](com-wrappers.md)
- [.NET Framework Bileşenlerini COM'da Gösterme](../../framework/interop/exposing-dotnet-components-to-com.md)
- [.NET Core bileşenlerini COM 'a gösterme](../../core/native-interop/expose-components-to-com.md)
- [Birlikte Çalışma için .NET Türlerini Niteleme](qualify-net-types-for-interoperation.md)
- [Çalışma Zamanında Çağrılabilir Sarmalayıcı](runtime-callable-wrapper.md)
