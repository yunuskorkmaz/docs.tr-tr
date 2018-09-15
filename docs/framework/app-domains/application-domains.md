---
title: Uygulama Etki Alanları
ms.date: 03/30/2017
helpviewer_keywords:
- process boundaries for isolation
- application isolation
- application domains, about
- common language runtime, application domains
- application domains
- runtime, application domains
- isolation between applications
- code, verification process
- verification testing code
ms.assetid: 113a8bbf-6875-4a72-a49d-ca2d92e19cc8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ddf8f52ab98d0188235d8c9f97293adced4bfe90
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649401"
---
# <a name="application-domains"></a>Uygulama Etki Alanları
İşletim sistemleri ve çalışma zamanı ortamlarını normalde çeşit uygulamalar arasında yalıtım sağlar. Örneğin, Windows uygulamalarını yalıtmak için işlemleri kullanır. Bir uygulama içinde çalışan kodun ilgisiz başka uygulamaları olumsuz yönde etkilememesini sağlamak bu yalıtım gereklidir.  
  
 Uygulama etki alanları, güvenlik, güvenilirlik ve sürüm oluşturma ve derlemeleri kaldırma için bir yalıtım sınırı sağlar. Uygulama etki alanları genellikle uygulama çalıştırılmadan önce ortak dil çalışma zamanı önyüklemesinden sorumlu çalışma zamanı ana bilgisayarları tarafından oluşturulur.  
  
 Belgelerin bu bölümdeki konular, derlemeler arasında yalıtım sağlamak için uygulama etki alanları kullanın işlemleri açıklanmaktadır.  
  
 Bu genel bakış aşağıdaki bölümleri içerir:  
  
-   [Uygulamaları yalıtmanın faydaları](#benefits)  
  
-   [Başvuru](#reference)  
  
<a name="benefits"></a>   
## <a name="the-benefits-of-isolating-applications"></a>Uygulamaları yalıtmanın faydaları  
 Tarihsel olarak, işlem sınırları aynı bilgisayar üzerinde çalışan uygulamaları yalıtmak için kullanılmış. Her uygulama, aynı bilgisayarda çalışan diğer uygulamalardan yalıtan ayrı bir işlemde içine yüklenir.  
  
 Uygulamalar, bellek adresleri işlem göreli olduğu için yalıtılmıştır; bir işlemden diğerine geçirilen bir bellek işaretçi herhangi anlamlı bir şekilde hedef işlem içinde kullanılamaz. Ayrıca, iki işlem arasında doğrudan arama yapamazsınız. Bunun yerine, bir yönlendirme düzeyi sağlayan proxy'ler kullanmanız gerekir.  
  
 (Yönetici doğrulamayı atlama izni vermedikçe) çalıştırılmadan önce yönetilen kod bir doğrulama işleminden geçirilmelidir. Doğrulama işlemi, kodun geçersiz bellek adreslerine erişme veya içinde düzgün çalışması başarısız olmaya çalıştığı işlemin neden olabilecek başka bir eylem gerçekleştirmek deneyebilirsiniz olup olmadığını belirler. Doğrulama testinden geçen kod tür kullanımı uyumlu olarak kabul edilir. Tür-güvenli olarak kodu doğrulama yeteneği, harika olarak en çok daha düşük performans maliyetine bir işlem sınırı kadar yüksek yalıtım düzeyini sağlamak için ortak dil çalışma zamanı sağlar.  
  
 Uygulama etki alanları ortak dil çalışma zamanı, uygulamalar arasında yalıtım sağlamak için kullanabileceğiniz işleme daha güvenli ve verimli bir birim sağlayın. Ayrı işlemlerde bulunan, ancak çapraz işlem aramaları yapma veya işlemler arasında geçiş yapma ek yükü zorunda kalmadan var yalıtım aynı düzeyine sahip tek bir işlemde birden çok uygulama etki alanları çalıştırabilirsiniz. Önemli ölçüde çoklu uygulamaları tek bir işlem içinde çalıştırma yeteneği sunucu ölçeklenebilirliğini artırır.  
  
 Uygulamaları yalıtmanın Ayrıca uygulama güvenliği için önemlidir. Örneğin, denetimleri denetimleri birbirlerinin verilerine ve kaynaklarına erişemediğini şekilde tek bir tarayıcı işleminde çeşitli Web uygulamalarından çalıştırabilirsiniz.  
  
 Uygulama etki alanları tarafından sağlanan yalıtım aşağıdaki faydaları sağlar:  
  
-   Bir uygulamadaki hatalar diğer uygulamaları etkilemez. Tür kullanımı uyumlu kod bellek hatalarına neden olmadığından uygulama etki alanları kullanan bir etki alanında çalışan kodun işlemdeki diğer uygulamaları etkilememesini sağlar.  
  
-   Tek tek uygulamalar, tüm işlemi durdurmadan durdurulabilir. Uygulama etki alanları kullanarak, tek bir uygulama içinde çalışan kodun kaldırılmasını sağlar.  
  
    > [!NOTE]
    >  Tek tek derlemeleri veya türleri kaldıramazsınız. Tam bir etki alanının yüklemesi kaldırılabilir.  
  
-   Bir uygulamada çalışan kod doğrudan koda veya kaynaklara başka bir uygulamaya ait olamaz. Ortak dil çalışma zamanı, farklı uygulama etki alanlarındaki nesneler arasında doğrudan çağrıları engelleyerek bu yalıtımı zorlar. Etki alanları arasında geçen nesneler kopyalanamaz veya proxy tarafından erişilebilir. Nesne kopyalanırsa, yapılan nesne çağrısı yerel. Diğer bir deyişle arayan ve başvurulan nesne aynı uygulama etki alanındadır. Nesne bir proxy sunucusu üzerinden erişiliyorsa, nesneye çağrı uzak çağrıdır. Bu durumda arayan ve başvurulan nesne farklı uygulama etki alanlarındadır. Etki alanları arası çağrıları, iki işlem arasında veya iki makine arasında çağrıları olarak aynı uzak çağrı altyapısını kullanır. Bu nedenle, başvurulan nesne için meta veriler, yöntem çağrısının JIT olarak derlenmiş doğru olmasını izin vermek için her iki uygulama etki alanları için kullanılabilir olmalıdır. Arama etki alanı için çağrılan nesne meta verilerine erişimi yoksa, derleme türünde bir özel durum ile başarısız olabilir **System.IO.FileNotFound**. Bkz: [uzak nesneleri](https://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58) daha fazla ayrıntı için. Etki alanları arasında nesnelerin nasıl erişilebileceğini belirleme mekanizması nesne tarafından belirlenir. Daha fazla bilgi için bkz. <xref:System.MarshalByRefObject?displayProperty=nameWithType>.  
  
-   Kodun çalışma biçiminin kapsamı içinde çalıştığı uygulama tarafından. Diğer bir deyişle, uygulama etki alanı, uygulama sürümü ilkeleri, eriştiği uzak derleme ve etki alanına yüklenen derlemelerin bulunacağı hakkında bilgi konumu gibi yapılandırma ayarlarını sağlar.  
  
-   Koda verilen izinler, kodun çalıştığı uygulama etki alanı tarafından denetlenebilir.  
  
  
## <a name="application-domains-and-assemblies"></a>Uygulama Etki Alanları ve Derlemeler  
 Bu konuda uygulama etki alanları ve derlemeler arasındaki ilişki açıklanmaktadır. Bir derlemenin içerdiği kodu yürütmeden önce derlemeyi bir uygulama etki alanına yüklemeniz gerekir. Tipik bir uygulamayı çalıştırmak, bir uygulama etki alanına birkaç derlemenin yüklenmesine neden olur.  
  
 Bir derlemenin yüklenme şekli, onun işlemdeki birden çok uygulama etki alanı ile paylaşılabilen anlık (JIT) derlenmiş kod olup olmadığını ve derlemenin işlemden kaldırılabilip kaldırılamayacağını belirler.  
  
-   Eğer bir derleme etki alanından bağımsız olarak yüklenirse, aynı güvenlik izni kümesine sahip olan tüm uygulama etki alanları aynı JIT olarak derlenmiş kodunu paylaşabilir ve bu da uygulamanın gerektirdiği belleği azaltır. Ancak, derleme işlemden asla kaldırılamaz.  
  
-   Eğer bir derleme etki alanından bağımsız olarak yüklenmezse, yüklendiği tüm uygulama etki alanlarında JIT olarak derlenmelidir. Ancak derleme, yüklü olduğu tüm uygulama etki alanları kaldırılarak işlemden kaldırılabilir.  
  
 Çalışma zamanı konak ortamı, çalışma zamanını bir işleme yüklerken derlemeleri etki alanından bağımsız olarak yükleyip yüklemeyeceğini belirler. Yönetilen uygulamalar için, <xref:System.LoaderOptimizationAttribute> özniteliğini işlem için giriş noktası metoduna uygulayın ve ilişkili <xref:System.LoaderOptimization> sabit listesinden bir değer belirtin. Ortak dil çalışma zamanını barındıran yönetilmeyen uygulamaları belirtmek için uygun bayrağı çağırdığınızda [CorBindToRuntimeEx işlevi](../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) yöntemi.  
  
 Etki alanından bağımsız derlemeleri yüklemek için üç seçenek vardır:  
  
- <xref:System.LoaderOptimization.SingleDomain?displayProperty=nameWithType>, her zaman etki alanından bağımsız olarak yüklenen Mscorlib dışındaki hiçbir derlemeyi etki alanından bağımsız olarak yüklemez. Ana işlemde tek bir uygulamada çalışırken yaygın olarak kullanıldığı için bu ayar tek etki alanı adı verilir.

- <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType>, tüm derlemeleri etki alanından bağımsız yükler. İşlemde tamamı aynı kodu çalıştıran birden çok uygulama etki alanı olduğunda bu ayarı kullanın.

- <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, tanımlayıcı ada sahip olan derlemeleri, kendileri ve tüm bağımlılıkları genel bütünleştirilmiş kod önbelleğinde yüklü ise, etki alanından bağımsız olarak yükler. Diğer derlemeler yüklü oldukları her uygulama etki alanı için ayrı olarak yüklenip JIT olarak derlenirler ve bu nedenle işlemden kaldırılabilirler. Aynı işlemde birden çok uygulama çalıştırırken veya işlemden kaldırılması gereken birden çok uygulama etki alanı ve derleme tarafından paylaşılan bir derleme karışımına sahipseniz bu ayarı kullanın.
  
 JIT olarak derlenmiş kod, <xref:System.Reflection.Assembly.LoadFrom%2A> sınıfının <xref:System.Reflection.Assembly> yöntemi kullanarak load-from bağlamı içine yüklenen derlemeler için ya da <xref:System.Reflection.Assembly.Load%2A> yönteminin bayt dizilerini belirten aşırı yüklemeleri kullanılarak görüntülerden yüklenen derlemeler için paylaşılamaz.  
  
 Kullanılarak yerel koda derlenen derlemeler [Ngen.exe (yerel Görüntü Oluşturucu)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) oldukları bir işleme ilk kez etki alanından bağımsız yüklerse, uygulama etki alanları arasında paylaşılabilir.  
  
 Uygulama giriş noktasını içeren derleme için JIT olarak derlenmiş kod, yalnızca tüm bağımlılıkları paylaşılabiliyorsa paylaşılır.  
  
 Etki alanından bağımsız bir derleme JIT olarak birden çok kez derlenebilir. Örneğin, iki uygulama etki alanının güvenlik izni kümeleri farklıysa, aynı JIT olarak derlenmiş kodu paylaşamazlar. Ancak, JIT olarak derlenmiş derlemenin her kopyası, aynı izin kümesine sahip olan diğer uygulama etki alanlarıyla paylaşılabilir.  
  
 Derlemeleri etki alanından bağımsız olarak yükleyip yüklemeyeceğinize karar verdiğinizde, bellek kullanımı ve diğer performans etmenleri arasında bir takas yapmanız gerekir.  
  
-   Etki alanından bağımsız derlemeler için statik verilere ve yöntemlere olan erişim, derlemeleri yalıtmak gerektiği için daha yavaştır. Statik alanlardaki nesnelere olan başvuruların etki alanı sınırlarını geçmesini engellemek için derlemeye erişen tüm uygulama etki alanlarının, statik verinin ayrı kopyalarına sahip olması gerekir. Sonuç olarak, çalışma zamanı bir çağıranı statik veri veya yöntemin uygun kopyasına yönlendirmek için ek mantık içerir. Bu ek mantık, çağrıyı yavaşlatır.  
  
-   Derleme etki alanından bağımsız olarak yüklendiğinde, derlemenin tüm bağımlılıkları konumlandırılıp yüklenmelidir çünkü etki alanından bağımsız olarak yüklenemeyen bir bağımlılık, derlemenin etki alanından bağımsız olarak yüklenmesini engeller.  
  
## <a name="application-domains-and-threads"></a>Uygulama Etki Alanları ve İş Parçacıkları  
 Uygulama etki alanı güvenlik, sürüm oluşturma, güvenilirlik ve yönetilen kod kaldırılması için bir yalıtım sınırı oluşturur. Bir iş parçacığı, kod yürütmek için ortak dil çalışma zamanı tarafından kullanılan işletim sistemi yapıdır. Çalışma zamanında tüm yönetilen kod, bir uygulama etki alanına yüklenir ve bir veya daha fazla yönetilen iş parçacıkları tarafından çalıştırılır.  
  
 Uygulama etki alanları ve iş parçacıkları arasında bire bir ilişki değil. Birkaç iş parçacığı herhangi bir zamanda tek bir uygulama etki alanında yürütebilir ve belirli bir iş parçacığında bir tek bir uygulama etki alanına sınırlı değildir. Diğer bir deyişle, iş parçacığı uygulama etki alanı sınırları geçilecek ücretsizdir; her uygulama etki alanı için yeni bir iş parçacığı oluşturulmaz.  
  
 Belirli bir zamanda, her iş parçacığı bir uygulama etki alanında yürütür. Sıfır, bir veya birden çok iş parçacığı herhangi bir belirli uygulama etki alanında yürütülüyor. Çalışma zamanını hangi iş parçacıkları hangi uygulama etki alanlarında çalışan izler. Etki alanı içinde bir iş parçacığının yürütülmekte herhangi bir zamanda çağırarak bulabilirsiniz <xref:System.Threading.Thread.GetDomain%2A?displayProperty=nameWithType> yöntemi.  
  
### <a name="application-domains-and-cultures"></a>Uygulama etki alanları ve kültürler  
 Tarafından temsil edilen kültürü bir <xref:System.Globalization.CultureInfo> nesne, iş parçacıkları ile ilişkilidir. Kullanarak şu anda yürütülen iş parçacığıyla ilişkilendirilmiş kültürü alabilirsiniz <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliğini alma veya ayarlama kullanarak o anda yürütülen iş parçacığıyla ilişkilendirilmiş kültürü <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği. Bir iş parçacığıyla ilişkilendirilmiş kültürü kullanarak açıkça ayarlanmış <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği devam iş parçacığı uygulama etki alanı sınırları geçtiğinde bu iş parçacığı ile ilişkilendirilecek. Aksi takdirde, herhangi bir zamanda iş parçacığıyla ilişkilendirilmiş kültürü değeri tarafından belirlenir <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> iş parçacığı yürütüyordur uygulama etki alanındaki özelliği:  
  
-   Özelliğinin değeri değilse `null`, özellik tarafından döndürülen iş parçacığı ile ilişkili kültürüdür (ve bu nedenle tarafından döndürülen <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> ve <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özellikleri).  
  
-   Özelliğinin değeri ise `null`, geçerli sistem kültürü iş parçacığı ile ilişkilidir.  
  
## <a name="programming-with-application-domains"></a>Uygulama Etki Alanlarıyla Programlama  
 Uygulama etki alanları genellikle programlı olarak çalışma zamanı ana bilgisayarları tarafından oluşturulur ve değiştirilir. Ancak, bazen bir uygulama programı da uygulama etki alanları ile birlikte çalışmak isteyebilir. Örneğin, bir uygulama programı, tüm uygulamayı durdurmasına gerek kalmadan etki alanını (ve bileşeni) kaldırabilmek için bir etki alanına bir uygulama bileşeni yükleyebilir.  
  
 <xref:System.AppDomain> Uygulama etki alanları için programlama arabirimidir. Bu sınıf, etki alanları oluşturmak ve kaldırmak, etki alanlarında türlerin örneklerini oluşturmak ve uygulama etki alanı kaldırma gibi belirli bildirimlere kaydolmak için metotlar içerir. Aşağıdaki tabloda yaygın olarak kullanılan <xref:System.AppDomain> yöntemleri.  
  
|AppDomain Yöntemi|Açıklama|  
|----------------------|-----------------|  
|<xref:System.AppDomain.CreateDomain%2A>|Yeni bir uygulama etki alanı oluşturur. Bu yöntemin bir <xref:System.AppDomainSetup> nesnesi belirten bir aşırı yüklemesini kullanmanız önerilir. Bu; yeni bir etki alanının uygulama temel dizini veya uygulamanın kök dizini, etki alanı için yapılandırma dosyasının konumu ve ortak dil çalışma zamanının etki alanına yeni derlemeler yüklemek için kullanacağı arama yolu gibi özelliklerini ayarlamak için tercih edilen yöntemdir.|  
|<xref:System.AppDomain.ExecuteAssembly%2A> ve <xref:System.AppDomain.ExecuteAssemblyByName%2A>|Uygulama etki alanındaki bir derlemeyi yürütür. Bu bir örnek yöntemi olduğundan, atıfta bulunduğunuz başka bir uygulama etki alanındaki kodu yürütmek için kullanılabilir.|  
|<xref:System.AppDomain.CreateInstanceAndUnwrap%2A>|Uygulama etki alanında belirtilen bir türün bir örneğini oluşturur ve bir proxy döndürür. Oluşturulan türü içeren derlemenin, bu derlemeyi çağıran derlemeye yüklenmesini engellemek için kullanın.|  
|<xref:System.AppDomain.Unload%2A>|Etki alanının düzgün bir şekilde kapatılmasını gerçekleştirir. Uygulama etki alanı, etki alanındaki tüm iş parçacıkları durmadan veya etki alanının dışında olmadan kaldırılmaz.|  
  
> [!NOTE]
>  Ortak dil çalışma zamanı, genel yöntemlerin serileştirilmesini desteklemediğinden, temsilciler kullanılarak diğer uygulama etki alanlarındaki genel yöntemler yürütülemez.  
  
 Ortak dil çalışma zamanı Ana Bilgisayarları Arabirimleri Bildirimi'nde açıklanan yönetilmeyen arabirimler de uygulama etki alanlarına erişim sağlar. Çalışma zamanı ana bilgisayarları, yönetilmeyen koddan arabirimler kullanarak bir işlem içinde uygulama etki alanları oluşturabilir veya onlara erişebilir.  
  
## <a name="complusloaderoptimization-environment-variable"></a>COMPLUS_LoaderOptimization Ortam Değişkeni  
 Yürütülebilir uygulamanın varsayılan yükleyici iyileştirme ilkesini ayarlayan ortam değişkeni.  
  
### <a name="syntax"></a>Sözdizimi  
  
```  
COMPLUS_LoaderOptimization = 1  
```  
  
### <a name="remarks"></a>Açıklamalar  
 Tipik bir uygulaması, içerdiği kodu yürütmeden önce çeşitli derlemeler uygulama etki alanına yükler.  
  
 Derlemenin yüklenme şekli, onun just-in-time (JIT) derlenmiş kod olup olmadığını belirler işlemde birden çok uygulama etki alanı tarafından paylaşılabilir.  
  
-   Bir derleme yüklenen etki alanından bağımsız ise, aynı güvenlik verme kümesi paylaşan tüm uygulama etki alanları aynı JIT olarak derlenmiş kod paylaşabilirsiniz. Bu uygulamanın gerektirdiği belleği azaltır.  
  
-   Bir derleme yüklenen etki alanı nötr değilse, bu yüklenir yüklenmez ve Yükleyici uygulama etki alanları arasında iç kaynakları paylaşmamalıdır her uygulama etki alanı içinde JIT olarak derlenmiş olmalıdır.  
  
 COMPLUS_LoaderOptimization ortam bayrağı 1 olarak ayarlandığında, etki alanından bağımsız şekilde SingleDomain bilinen tüm derlemeleri yüklemeye çalışma zamanında konak zorlar. SingleDomain, etki alanından bağımsız olarak, her zaman etki alanından bağımsız yüklenen Mscorlib dışındaki hiçbir derlemeyi yükler. Ana işlemde tek bir uygulamada çalışırken yaygın olarak kullanıldığı için bu ayar tek etki alanı adı verilir.  
  
> [!CAUTION]
>  COMPLUS_LoaderOptimization ortam bayrağı tanı kullanılmak üzere tasarlanmıştır ve test senaryoları. Bayrağın açık olması ciddi artışına neden ve bellek kullanımı.  
  
### <a name="code-example"></a>Kod Örneği  
 Yüklenmeyeceğini tüm derlemelerin etki alanından bağımsız olarak IISADMIN için zorlamak için hizmet ekleyerek ulaşılabilecek `COMPLUS_LoaderOptimization=1` hkey_local_machıne\system\currentcontrolset\services\ıısadmın anahtarında ortam Çoklu dize değeri.  
  
```  
Key = HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN  
Name = Environment  
Type = REG_MULTI_SZ  
Value (to append) = COMPLUS_LoaderOptimization=1  
```  
  
<a name="reference"></a>   
## <a name="reference"></a>Başvuru  
 <xref:System.MarshalByRefObject?displayProperty=nameWithType>
