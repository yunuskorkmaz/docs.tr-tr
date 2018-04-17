---
title: COM Aranabilir Sarmalayıcısı
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 270d7e85491f0f4ada797910d4fc12c1a14be625
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="com-callable-wrapper"></a>COM Aranabilir Sarmalayıcısı
COM istemcisi .NET nesnesi aradığında, ortak dil çalışma zamanı yönetilen nesneyi ve nesne için bir COM aranabilir sarmalayıcısı (saat) oluşturur. Bir .NET nesnesine başvuru için doğrudan COM istemcileri saatin tersi YÖNDE bir proxy olarak yönetilen nesne için kullanın.  
  
 Çalışma zamanı hizmetlerinin isteyen COM istemcileri sayısından bağımsız olarak yönetilen bir nesne için tam olarak bir saat oluşturur. Aşağıdaki çizimde gösterildiği gibi birden çok COM istemcileri INew arabirimi kullanıma sunan saatin tersi YÖNDE başvuru basılı tutabilirsiniz. Saatin tersi YÖNDE, sırasıyla arabirimini uygulayan yönetilen nesne için tek bir başvuru tutar ve atık toplanır. COM ve .NET istemcileri, istekleri için aynı anda aynı yönetilen nesne üzerinde hale getirebilirsiniz.  
  
 ![COM aranabilir sarmalayıcısı](./media/ccw.gif "saatin tersi yönde")  
COM aranabilir sarmalayıcısı .NET nesnelere erişme  
  
 COM aranabilir sarmalayıcılar, .NET Framework içinde çalışan diğer sınıflara görünmez. Yönetilen ve yönetilmeyen kodu arasında çağrılarını sıralamakta kendi birincil amacı olan; Ancak, CCWs nesne kimliği ve bunlar sarmalamak yönetilen nesnelerin nesne ömrü yönetin.  
  
## <a name="object-identity"></a>Nesne Kimliği  
 Çalışma zamanı gerektiği gibi bellekteki nesne hareket etmek çalışma zamanı sağlayan kendi çöpünün toplanma yığın, gelen .NET nesnesi için bellek ayırır. Buna karşılık, çalışma zamanı sarmalayıcı doğrudan başvurmak COM istemcileri için olası hale getirerek noncollected bir öbek gelen için saatin tersi YÖNDE bellek ayırır.  
  
## <a name="object-lifetime"></a>Nesne ömrü  
 Sarmaladığı .NET istemcilerin aksine, saatin tersi YÖNDE başvuru-geleneksel COM şekilde sayılır. Saatin tersi YÖNDE başvuru sayısı sıfır ulaştığında sarmalayıcı yönetilen nesne üzerinde kendi başvuru serbest bırakır. Kalan başvuru ile yönetilen bir nesnenin sonraki çöp toplama döngüsü sırasında toplanır.  
  
## <a name="simulating-com-interfaces"></a>COM arabirimleri benzetimini yapma

Saatin tersi YÖNDE tüm ortak, COM görünebilir arabirimler, veri türleri ve dönüş değerleri COM istemcilere arabirimi tabanlı etkileşim COM'ın zorlama ile tutarlı bir şekilde kullanıma sunar. COM istemcisi için bir .NET Framework nesne üzerinde yöntemleri çağrılırken bir COM nesnesinin yöntemlerde çağırmak için aynıdır.  
  
 Bu sorunsuz bir yaklaşım oluşturmak için saatin tersi YÖNDE geleneksel COM arabirimleri gibi üreten **IUnknown** ve **IDispatch**. Aşağıdaki çizimde gösterildiği gibi saatin tersi YÖNDE sarmaladığı .NET nesnesi üzerinde tek bir başvuru tutar. COM istemcisi ve .NET nesne birbiriyle CCW. proxy ve saplama yapımı etkileşim  
  
 ![COM arabirimleri](./media/ccwwithinterfaces.gif "ccwwithinterfaces")  
COM arabirimleri ve COM aranabilir sarmalayıcısı  
  
 Yönetilen ortamda bir sınıf tarafından açıkça uygulanan arabirimler gösterme ek olarak, .NET Framework uygulamaları nesne adına aşağıdaki tabloda listelenen COM arabirimleri sağlar. Bir .NET sınıfı, kendi uygulama bu arabirimleri sağlayarak varsayılan davranışı geçersiz kılabilirsiniz. Ancak, çalışma zamanı uygulamasını her zaman sağlar **IUnknown** ve **IDispatch** arabirimleri.  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|**IDispatch**|Geç bağlama türü bir mekanizma sağlar.|  
|**IerrorInfo**|Hata, kaynağı, bir Yardım dosyası, Yardım içeriği ve hata tanımlı arabirimi GUID metinsel açıklaması sağlar (her zaman **GUID_NULL** .NET sınıfları için).|  
|**IprovideClassInfo**|Erişim kazanmak COM istemcilerinde etkinleştirir **ITypeInfo** yönetilen bir sınıf tarafından uygulanan arabirimi.|  
|**IsupportErrorInfo**|Yönetilen Nesne destekleyip desteklemediğini belirlemek bir COM istemcisi sağlar **IErrorInfo** arabirimi. Bu durumda, son özel durum nesnesi için bir işaretçi almak istemci sağlar. Tüm yönetilen türleri Destek **IErrorInfo** arabirimi.|  
|**ITypeInfo**|Tlbexp.exe tarafından üretilen türü bilgileri tam olarak aynıdır bir sınıf için tür bilgiler sağlar.|  
|**IUnknown**|Standart uygulamasını sağlar **IUnknown** hangi COM istemcisi saatin tersi YÖNDE ömrü yönetir ve türü zorlama sağlar arabirimi.|  
  
 Yönetilen bir sınıf, aşağıdaki tabloda açıklanan COM arabirimleri de sağlayabilirsiniz.  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|(\_*Classname*) sınıf arabirimi|Çalışma zamanı tarafından kullanıma sunulan ve açıkça tanımlanmış arabirimi, tüm ortak arabirimleri, yöntemler, özellikler ve yönetilen bir nesne üzerinde açıkça gösterilen alanları kullanıma sunar.|  
|**IConnectionPoint** ve **IConnectionPointContainer**|Temsilci tabanlı olaylar (olay aboneleri kaydettirmek için bir arabirim) kaynak nesneler için arabirim.|  
|**Idispatchex**|Sınıf uyguluyorsa çalışma zamanı tarafından sağlanan arabirim **IExpando**. **Idispatchex** arabirimi uzantısıdır **IDispatch** aksine, arabirim **IDispatch**, numaralandırma, ekleme, silme, sağlar ve büyük küçük harfe duyarlı üyeleri çağrılıyor.|  
|**IEnumVARIANT**|Arabirim koleksiyon türü sınıfları için sınıf uyguluyorsa, koleksiyonundaki nesneleri numaralandırır **IEnumerable**.|  
  
## <a name="introducing-the-class-interface"></a>Sınıf arabirimi Tanıtımı  
 Açıkça yönetilen kodda tanımlı değil, sınıf arabirimi tüm genel yöntemler, özellikler, alanları ve .NET nesne üzerinde açıkça gösterilen olayları gösteren bir arabirimdir. Bu arabirim, bir çift veya yalnızca gönderme arabirimi olabilir. Sınıf arabirimi bir çizgiyle öncesinde .NET sınıfın kendisi adını alır. Örneğin, Mammal sınıfı için sınıf arabirimidir \_Mammal.  
  
 Türetilen sınıflar için sınıf arabirimi tüm genel yöntemler, özellikler ve temel sınıfın alanları gösterir. Türetilmiş sınıf ayrıca her taban sınıfı için sınıf arabirimi sunar. Örneğin, sınıf Mammal MammalSuperclass sınıfını genişletir, kendisi System.Object genişletir, COM istemcileri için .NET nesne düzenlemenizi sağlayan üç adlı arabirimleri sınıf \_memeli, \_MammalSuperclass, ve \_nesne.  
  
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
    void  Eat();  
    void  Breathe():  
    void  Sleep();  
}  
```  
  
 COM istemcisi adlı bir sınıf arabirimi için bir işaretçi edinebilirsiniz `_Mammal`, Tür Kitaplığı'nda açıklanan, [tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) aracı oluşturur. Varsa `Mammal` sınıfı uygulanan bir veya daha fazla arabirimin, arabirimler coclass'ı altında görünür.  
  
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
  
 Sınıf arabirimi oluşturma isteğe bağlıdır. Varsayılan olarak, COM birlikte çalışma için bir tür kitaplığı dışarı her sınıf için bir yalnızca gönderme arabirimi oluşturur. Engellemek ya da bu arabirimi otomatik olarak oluşturulmasını uygulayarak değiştirmek <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> sınıfınıza. Yönetilen sınıflar com'da gösterme görev sınıf arabirimi kolaylaştırabilir rağmen kullanımları sınırlıdır.  
  
> [!CAUTION]
>  Sınıf arabirimi kullanarak, açıkça, kendi tanımlama yerine yönetilen sınıfınızın gelecekteki sürüm karmaşık hale getirebilir. Sınıf arabirimi kullanmadan önce aşağıdaki yönergeleri okuyun.  
  
### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a>COM istemcileri sınıf arabirimi oluşturmak yerine kullanmak için açık bir arabirim tanımlayın.  
 COM birlikte çalışma sınıf arabirimi otomatik olarak oluşturduğundan, sonrası sürüm değişiklikleri sınıfınıza ortak dil çalışma zamanı tarafından kullanıma sunulan sınıfı arabiriminin düzenini değiştirebilirsiniz. COM istemcileri bir arabirim düzeninde değişiklikler işlemek genellikle hazırlıksız olduğundan, sınıf üyesi düzenini değiştirirseniz, bunlar bölün.  
  
 Bu kılavuz, COM istemcileri için sunulan arabirimleri değiştirilemez kalması gereken kavram eklenir. COM istemcileri yanlışlıkla arabirimi düzeni sıralayarak çiğnemekten riskini azaltmak için tüm değişiklikleri açıkça arabirimleri tanımlayarak sınıfa arabirimi düzeninden yalıtma.  
  
 Kullanım **ClassInterfaceAttribute** sınıf arabirimi otomatik olarak oluşturulmasını disengage ve aşağıdaki kod parçası gösterildiği gibi sınıf için açık bir arabirim uygulamak için:  
  
```vb  
<ClassInterface(ClassInterfaceType.None)>Public Class LoanApp  
    Implements IExplicit  
    Sub M() Implements IExplicit.M  
…  
End Class  
```  
  
```csharp  
[ClassInterface(ClassInterfaceType.None)]  
public class LoanApp : IExplicit {  
    void M();  
}  
```  
  
 **ClassInterfaceType.None** değer sınıfı meta veriler için bir tür kitaplığı dışarı aktardığınızda oluşturulan sınıf arabirimi engeller. Önceki örnekte, COM istemcileri erişebilir `LoanApp` yalnızca aracılığıyla sınıf `IExplicit` arabirimi.  
  
### <a name="avoid-caching-dispatch-identifiers-dispids"></a>Gönderme tanımlayıcıları (DISPID değerleri) önbelleğe alma kaçının
 Sınıf arabirimi kullanarak, komut dosyası kullanan istemciler, Microsoft Visual Basic 6.0 istemciler veya arabirim üyelerinin DISPID değerleri önbelleğe almaz herhangi geç bağlama istemci için kabul edilebilir bir seçenektir. Geç bağlama etkinleştirmek için arabirim üyeleri DISPID değerleri tanımlayın.  
  
 Sınıf arabirimi için arabirim üye konumda DISPID değerleri nesil dayanır. Üye sırasını değiştirirseniz ve sınıf için bir tür kitaplığı dışarı aktarma, sınıf arabiriminde oluşturulan DISPID değerleri değiştirir.  
  
 Geç bağlama COM istemcileri sınıf arabirimi kullanılırken çiğnemekten kaçının uygulamak **ClassInterfaceAttribute** ile **ClassInterfaceType.AutoDispatch** değeri. Bu değer yalnızca gönderme sınıfı arabirimini uygulayan ancak tür kitaplığı arabirimi açıklamasından atlar. Bir arabirim açıklaması istemciler DISPID değerleri, derleme zamanı önbelleğine erişemiyor. Bu sınıf arabirimi için varsayılan arabirim türü olsa da, öznitelik değeri açıkça uygulayabilirsiniz.  
  
```vb  
<ClassInterface(ClassInterfaceType.AutoDispatch)> Public Class LoanApp  
    Implements IAnother  
    Sub M() Implements IAnother.M  
…  
End Class  
```  
  
```csharp  
[ClassInterface(ClassInterfaceType.AutoDispatch]  
public class LoanApp : IAnother {  
    void M();  
}  
```  
  
 Çalışma zamanında arabirim üyesini DISPID almak için COM istemcileri çağırabilirsiniz **IDispatch.GetIdsOfNames**. Arabirimdeki bir yöntemi çağırmak için bağımsız değişken olarak döndürülen DISPID geçirmek **IDispatch.Invoke**.  
  
### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a>Sınıf arabirimi için çift arabirim seçeneği kullanılarak kısıtlayın.  
 Çift arabirimler arabirim üyeleri COM istemcileri tarafından erken ve geç bağlama etkinleştirin. Tasarım zamanında ve test sırasında sınıf arabirimi için çift ayarlamak yararlı olabilir. Yönetilen bir sınıfın (ve temel sınıflarından), hiçbir zaman olacaktır değiştirilmiş, bu da kabul edilebilir bir seçenektir. Diğer durumlarda, sınıf arabirimi çift ayarlamamaya özen gösterin.  
  
 Otomatik olarak oluşturulan bir çift arabirim nadir durumlarda uygun olabilir; Ancak, daha sık bu sürümüyle ilgili karmaşıklık oluşturur. Örneğin, bir türetilmiş sınıfta sınıfı arabirimini kullanarak COM istemcileri için temel sınıf kolayca değişikliklerle bozulabilir. Bir üçüncü taraf temel sınıf sağlar sınıfı arabiriminin düzenini dışında denetiminiz olur. Daha fazla, yalnızca gönderme arabirimi çift arabirim (**ClassInterface.AutoDual**) verilen tür kitaplığı sınıfı arabiriminde açıklamasını sağlar. Bu tür bir açıklama önbellek DISPID değerleri geç bağlama istemcilere çalışma zamanında önerir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>  
 [COM Sarmalayıcıları](com-wrappers.md)  
 [.NET Framework Bileşenlerini COM'da Gösterme](exposing-dotnet-components-to-com.md)  
 [Birlikte Çalışma için .NET Türlerini Niteleme](qualifying-net-types-for-interoperation.md)  
 [Çalışma Zamanında Çağrılabilir Sarmalayıcı](runtime-callable-wrapper.md)