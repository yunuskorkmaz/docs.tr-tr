---
title: Uygulama etki alanları
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
ms.openlocfilehash: a5c9f4248e060d231941269f39cadbc7147ce27f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399877"
---
# <a name="application-domains"></a>Uygulama etki alanları

İşletim sistemleri ve çalışma zamanı ortamları genellikle uygulamalar arasında bir yalıtım biçimi sağlar. Örneğin, Windows uygulamaları yalıtmak için süreçler kullanır. Bu yalıtım, bir uygulamada çalışan kodun, ilgisiz diğer uygulamaları olumsuz şekilde etkilememesini sağlamak için gereklidir.  
  
 Uygulama etki alanları güvenlik, güvenilirlik ve sürüm oluşturma ve derleme kaldırma için bir yalıtım sınırı sağlar. Uygulama etki alanları genellikle, bir uygulamanın çalıştırılmasından önce ortak dil çalışma zamanının önyüklemesinden sorumlu olan çalışma zamanı ana bilgisayarları tarafından oluşturulur.  
  
## <a name="the-benefits-of-isolating-applications"></a>Uygulamaları yalıtma avantajları

 Tarihsel olarak, işlem sınırları aynı bilgisayarda çalışan uygulamaları yalıtmak için kullanılır. Her uygulama ayrı bir işleme yüklenir ve uygulamayı aynı bilgisayarda çalışan diğer uygulamalardan yalıtır.  
  
 Bellek adresleri işlem göreli olduğundan uygulamalar yalıtılmıştır; bir işlemden diğerine geçirilen bir bellek işaretçisi, hedef işlemde anlamlı hiçbir şekilde kullanılamaz. Ayrıca, iki işlem arasında doğrudan çağrı yapamazsınız. Bunun yerine, bir yöneltme düzeyi sağlayan proxy 'leri kullanmanız gerekir.  
  
 Yönetilen kodun çalıştırılabilmesi için önce bir doğrulama işleminden geçirilmesi gerekir (yönetici doğrulamayı atlama izni verilmemişse). Doğrulama işlemi, kodun geçersiz bellek adreslerine erişmeyi deneyebilir veya çalıştığı işlemin düzgün bir şekilde çalışamamasına neden olabilecek başka bir eylem gerçekleştirip gerçekleştirmeyeceğini belirler. Doğrulama testini geçiren kod, tür açısından güvenli olarak kabul edilir. Kodu tür kullanımı güvenli olarak doğrulayabilme özelliği, ortak dil çalışma zamanının işlem sınırı olarak çok daha düşük performans maliyetinde bir yalıtım düzeyi sağlamasına olanak sağlar.  
  
 Uygulama etki alanları, ortak dil çalışma zamanının uygulamalar arasında yalıtım sağlamak için kullanabileceği daha güvenli ve çok yönlü bir işlem birimi sağlar. Çeşitli uygulama etki alanlarını ayrı işlemlerde bulunan aynı yalıtım düzeyine sahip tek bir işlemde çalıştırabilirsiniz, ancak işlemler arasında çapraz işlem çağrıları yapma veya işlemler arasında geçiş yapmak için ek yük kalmaz. Tek bir işlemde birden çok uygulama çalıştırma özelliği, sunucu ölçeklenebilirliğini önemli ölçüde artırır.  
  
 Uygulamaları yalıtmak uygulama güvenliği için de önemlidir. Örneğin, denetimlerin her bir veri ve kaynağa erişemeyeceği şekilde, tek bir tarayıcı işleminde çeşitli Web uygulamalarından denetimleri çalıştırabilirsiniz.  
  
 Uygulama etki alanları tarafından sunulan yalıtımın avantajları şunlardır:  
  
- Bir uygulamadaki hatalar diğer uygulamaları etkilemez. Tür kullanımı uyumlu kod bellek hatalarına neden olabileceğinden, uygulama etki alanlarının kullanılması, bir etki alanında çalışan kodun işlemdeki diğer uygulamaları etkilememesini sağlar.  
  
- Tek tek uygulamalar, tüm işlem durdurulmadan durdurulabilir. Uygulama etki alanlarının kullanılması, tek bir uygulamada çalışan kodu kaldırmayı sağlar.  
  
    > [!NOTE]
    > Ayrı derlemeler veya türler kaldırılamaz. Yalnızca bir etki alanı kaldırılabilir.  
  
- Bir uygulamada çalışan kod, başka bir uygulamadan koda veya kaynaklara doğrudan erişemez. Ortak dil çalışma zamanı, farklı uygulama etki alanlarındaki nesneler arasındaki doğrudan çağrıları önleyerek bu yalıtımı zorlar. Etki alanları arasında geçiş yapan nesneler, proxy tarafından kopyalanır veya erişilir. Nesne kopyalanırsa, nesnesine yapılan çağrı yereldir. Diğer bir deyişle, hem çağıran hem de başvurulan nesne aynı uygulama etki alanında olur. Nesnesine bir proxy üzerinden erişiliyorsa, nesnesine yapılan çağrı uzak olur. Bu durumda, çağıran ve başvurulan nesne farklı uygulama etki alanlarında. Çapraz etki alanı çağrıları, iki işlem arasındaki veya iki makine arasındaki çağrılarla aynı uzaktan çağrı altyapısını kullanır. Bu nedenle, başvurulan nesnenin meta verileri, yöntem çağrısının JıT olarak derlenmesine izin vermek için her iki uygulama etki alanı için de kullanılabilir olmalıdır. Çağıran etki alanının çağrılan nesnenin meta verilerine erişimi yoksa, derleme, türünde <xref:System.IO.FileNotFoundException>bir özel durumla başarısız olabilir. Daha fazla bilgi için bkz. [uzak nesneler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)). Nesneleri etki alanları genelinde nasıl erişilebileceğini belirleme mekanizması nesne tarafından belirlenir. Daha fazla bilgi için bkz. <xref:System.MarshalByRefObject?displayProperty=nameWithType>.  
  
- Kodun davranışı, çalıştığı uygulamanın kapsamına alınır. Diğer bir deyişle, uygulama etki alanı, uygulama sürüm ilkeleri, eriştiği uzak derlemelerin konumu ve etki alanına yüklenen derlemelerin nerede bulunacağı hakkında bilgi gibi yapılandırma ayarları sağlar.  
  
- Koda verilen izinler, kodun çalıştığı uygulama etki alanı tarafından denetlenebilir.  
  
## <a name="application-domains-and-assemblies"></a>Uygulama Etki Alanları ve derlemeler

 Bu bölüm, uygulama etki alanları ve derlemeler arasındaki ilişkiyi açıklar. Bir derlemenin içerdiği kodu yürütmeden önce derlemeyi bir uygulama etki alanına yüklemeniz gerekir. Tipik bir uygulamayı çalıştırmak, bir uygulama etki alanına birkaç derlemenin yüklenmesine neden olur.  
  
 Bir derlemenin yüklenme şekli, onun işlemdeki birden çok uygulama etki alanı ile paylaşılabilen anlık (JIT) derlenmiş kod olup olmadığını ve derlemenin işlemden kaldırılabilip kaldırılamayacağını belirler.  
  
- Eğer bir derleme etki alanından bağımsız olarak yüklenirse, aynı güvenlik izni kümesine sahip olan tüm uygulama etki alanları aynı JIT olarak derlenmiş kodunu paylaşabilir ve bu da uygulamanın gerektirdiği belleği azaltır. Ancak, derleme işlemden asla kaldırılamaz.  
  
- Eğer bir derleme etki alanından bağımsız olarak yüklenmezse, yüklendiği tüm uygulama etki alanlarında JIT olarak derlenmelidir. Ancak derleme, yüklü olduğu tüm uygulama etki alanları kaldırılarak işlemden kaldırılabilir.  
  
 Çalışma zamanı konak ortamı, çalışma zamanını bir işleme yüklerken derlemeleri etki alanından bağımsız olarak yükleyip yüklemeyeceğini belirler. Yönetilen uygulamalar için, <xref:System.LoaderOptimizationAttribute> özniteliğini işlem için giriş noktası metoduna uygulayın ve ilişkili <xref:System.LoaderOptimization> sabit listesinden bir değer belirtin. Ortak dil çalışma zamanını barındıran yönetilmeyen uygulamalar için [CorBindToRuntimeEx işlev](../unmanaged-api/hosting/corbindtoruntimeex-function.md) yöntemini çağırdığınızda uygun bayrağı belirtin.  
  
 Etki alanından bağımsız derlemeleri yüklemek için üç seçenek vardır:  
  
- <xref:System.LoaderOptimization.SingleDomain?displayProperty=nameWithType>, her zaman etki alanından bağımsız olarak yüklenen Mscorlib dışındaki hiçbir derlemeyi etki alanından bağımsız olarak yüklemez. Bu ayar, ana bilgisayar işlemde yalnızca tek bir uygulama çalıştırırken yaygın olarak kullanıldığından, tek etki alanı olarak adlandırılır.

- <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType>, tüm derlemeleri etki alanından bağımsız yükler. İşlemde tamamı aynı kodu çalıştıran birden çok uygulama etki alanı olduğunda bu ayarı kullanın.

- <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, tanımlayıcı ada sahip olan derlemeleri, kendileri ve tüm bağımlılıkları genel bütünleştirilmiş kod önbelleğinde yüklü ise, etki alanından bağımsız olarak yükler. Diğer derlemeler yüklü oldukları her uygulama etki alanı için ayrı olarak yüklenip JIT olarak derlenirler ve bu nedenle işlemden kaldırılabilirler. Aynı işlemde birden çok uygulama çalıştırırken veya işlemden kaldırılması gereken birden çok uygulama etki alanı ve derleme tarafından paylaşılan bir derleme karışımına sahipseniz bu ayarı kullanın.
  
 JIT olarak derlenmiş kod, <xref:System.Reflection.Assembly.LoadFrom%2A> sınıfının <xref:System.Reflection.Assembly> yöntemi kullanarak load-from bağlamı içine yüklenen derlemeler için ya da <xref:System.Reflection.Assembly.Load%2A> yönteminin bayt dizilerini belirten aşırı yüklemeleri kullanılarak görüntülerden yüklenen derlemeler için paylaşılamaz.  
  
 [Ngen. exe (yerel görüntü Oluşturucu)](../tools/ngen-exe-native-image-generator.md) kullanılarak yerel koda derlenmiş derlemeler, bir işleme ilk kez yüklendiklerinde etki alanı nötr olarak yüklenirse, uygulama etki alanları arasında paylaşılabilir.  
  
 Uygulama giriş noktasını içeren derleme için JIT olarak derlenmiş kod, yalnızca tüm bağımlılıkları paylaşılabiliyorsa paylaşılır.  
  
 Etki alanından bağımsız bir derleme JIT olarak birden çok kez derlenebilir. Örneğin, iki uygulama etki alanının güvenlik izni kümeleri farklıysa, aynı JIT olarak derlenmiş kodu paylaşamazlar. Ancak, JIT olarak derlenmiş derlemenin her kopyası, aynı izin kümesine sahip olan diğer uygulama etki alanlarıyla paylaşılabilir.  
  
 Derlemeleri etki alanından bağımsız olarak yükleyip yüklemeyeceğinize karar verdiğinizde, bellek kullanımı ve diğer performans etmenleri arasında bir takas yapmanız gerekir.  
  
- Etki alanından bağımsız derlemeler için statik verilere ve yöntemlere olan erişim, derlemeleri yalıtmak gerektiği için daha yavaştır. Statik alanlardaki nesnelere olan başvuruların etki alanı sınırlarını geçmesini engellemek için derlemeye erişen tüm uygulama etki alanlarının, statik verinin ayrı kopyalarına sahip olması gerekir. Sonuç olarak, çalışma zamanı bir çağıranı statik veri veya yöntemin uygun kopyasına yönlendirmek için ek mantık içerir. Bu ek mantık, çağrıyı yavaşlatır.  
  
- Derleme etki alanından bağımsız olarak yüklendiğinde, derlemenin tüm bağımlılıkları konumlandırılıp yüklenmelidir çünkü etki alanından bağımsız olarak yüklenemeyen bir bağımlılık, derlemenin etki alanından bağımsız olarak yüklenmesini engeller.  
  
## <a name="application-domains-and-threads"></a>Uygulama etki alanları ve iş parçacıkları

 Uygulama etki alanı, yönetilen kodun güvenliği, sürümü oluşturma, güvenilirlik ve kaldırılması için bir yalıtım sınırı oluşturur. İş parçacığı, kodu yürütmek için ortak dil çalışma zamanı tarafından kullanılan işletim sistemi yapısıdır. Çalışma zamanında, tüm yönetilen kodlar bir uygulama etki alanına yüklenir ve bir veya daha fazla yönetilen iş parçacığı tarafından çalıştırılır.  
  
 Uygulama etki alanları ve iş parçacıkları arasında bire bir bağıntı yoktur. Birçok iş parçacığı, belirli bir zamanda tek bir uygulama etki alanında yürütebilir ve belirli bir iş parçacığı tek bir uygulama etki alanına göre sınırlandırmaz. Diğer bir deyişle, iş parçacıkları, uygulama etki alanı sınırları arasında ücretsizdir; her uygulama etki alanı için yeni bir iş parçacığı oluşturulmaz.  
  
 Belirli bir zamanda, her iş parçacığı bir uygulama etki alanında yürütülür. Sıfır, bir veya birden çok iş parçacığı belirli bir uygulama etki alanında Yürütülüyor olabilir. Çalışma zamanı, uygulama etki alanlarında hangi iş parçacıklarının çalıştığını izler. Yöntemini çağırarak, <xref:System.Threading.Thread.GetDomain%2A?displayProperty=nameWithType> bir iş parçacığının yürütüldüğü etki alanını istediğiniz zaman bulabilirsiniz.

### <a name="application-domains-and-cultures"></a>Uygulama etki alanları ve kültürleri

 Bir <xref:System.Globalization.CultureInfo> nesneyle temsil edilen kültür, iş parçacıklarıyla ilişkilendirilir. <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> Özelliğini kullanarak şu anda yürütülmekte olan iş parçacığıyla ilişkili kültürü alabilir ve <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliğini kullanarak şu anda yürütülmekte olan iş parçacığıyla ilişkili kültürü alabilir ya da ayarlayabilirsiniz. Bir iş parçacığı ile ilişkili kültür <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği kullanılarak açıkça ayarlandıysa, iş parçacığı uygulama etki alanı sınırlarını aştığında bu iş parçacığı ile ilişkilendirilmeye devam eder. Aksi takdirde, belirli bir zamanda iş parçacığıyla ilişkili kültür, iş parçacığının yürütüldüğü uygulama etki alanındaki <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> özelliğin değeri tarafından belirlenir:  
  
- Özelliğin değeri değilse `null`, özelliği tarafından döndürülen kültür iş parçacığıyla ilişkilendirilir (ve bu nedenle <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> ve <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özellikleri tarafından döndürülür).  
  
- Özelliğin değeri ise `null`, geçerli sistem kültürü iş parçacığıyla ilişkilendirilir.  
  
## <a name="programming-with-application-domains"></a>Uygulama etki alanlarıyla programlama

 Uygulama etki alanları genellikle programlı olarak çalışma zamanı ana bilgisayarları tarafından oluşturulur ve değiştirilir. Ancak, bazen bir uygulama programı da uygulama etki alanları ile birlikte çalışmak isteyebilir. Örneğin, bir uygulama programı, tüm uygulamayı durdurmasına gerek kalmadan etki alanını (ve bileşeni) kaldırabilmek için bir etki alanına bir uygulama bileşeni yükleyebilir.  
  
 , <xref:System.AppDomain> Uygulama etki alanlarına yönelik programlama arabirimidir. Bu sınıf, etki alanları oluşturmak ve kaldırmak, etki alanlarında türlerin örneklerini oluşturmak ve uygulama etki alanı kaldırma gibi belirli bildirimlere kaydolmak için metotlar içerir. Aşağıdaki tabloda yaygın olarak kullanılan <xref:System.AppDomain> Yöntemler listelenmiştir.  
  
|AppDomain Yöntemi|Açıklama|  
|----------------------|-----------------|  
|<xref:System.AppDomain.CreateDomain%2A>|Yeni bir uygulama etki alanı oluşturur. Bu yöntemin bir <xref:System.AppDomainSetup> nesnesi belirten bir aşırı yüklemesini kullanmanız önerilir. Bu; yeni bir etki alanının uygulama temel dizini veya uygulamanın kök dizini, etki alanı için yapılandırma dosyasının konumu ve ortak dil çalışma zamanının etki alanına yeni derlemeler yüklemek için kullanacağı arama yolu gibi özelliklerini ayarlamak için tercih edilen yöntemdir.|  
|<xref:System.AppDomain.ExecuteAssembly%2A> ve <xref:System.AppDomain.ExecuteAssemblyByName%2A>|Uygulama etki alanındaki bir derlemeyi yürütür. Bu bir örnek yöntemi olduğundan, atıfta bulunduğunuz başka bir uygulama etki alanındaki kodu yürütmek için kullanılabilir.|  
|<xref:System.AppDomain.CreateInstanceAndUnwrap%2A>|Uygulama etki alanında belirtilen bir türün bir örneğini oluşturur ve bir proxy döndürür. Oluşturulan türü içeren derlemenin, bu derlemeyi çağıran derlemeye yüklenmesini engellemek için kullanın.|  
|<xref:System.AppDomain.Unload%2A>|Etki alanının düzgün bir şekilde kapatılmasını gerçekleştirir. Uygulama etki alanı, etki alanındaki tüm iş parçacıkları durmadan veya etki alanının dışında olmadan kaldırılmaz.|  
  
> [!NOTE]
> Ortak dil çalışma zamanı, genel yöntemlerin serileştirilmesini desteklemediğinden, temsilciler kullanılarak diğer uygulama etki alanlarındaki genel yöntemler yürütülemez.  
  
 Ortak dil çalışma zamanı Ana Bilgisayarları Arabirimleri Bildirimi'nde açıklanan yönetilmeyen arabirimler de uygulama etki alanlarına erişim sağlar. Çalışma zamanı ana bilgisayarları, yönetilmeyen koddan arabirimler kullanarak bir işlem içinde uygulama etki alanları oluşturabilir veya onlara erişebilir.  
  
## <a name="the-complus_loaderoptimization-environment-variable"></a>COMPLUS_LoaderOptimization ortam değişkeni

 Yürütülebilir bir uygulamanın varsayılan yükleyici en iyi duruma getirme ilkesini ayarlayan ortam değişkeni.  
  
### <a name="syntax"></a>Sözdizimi  
  
```env  
COMPLUS_LoaderOptimization = 1  
```  
  
### <a name="remarks"></a>Açıklamalar

 Tipik bir uygulama, içerdikleri kod yürütülene kadar bir uygulama etki alanına birçok derlemeyi yükler.  
  
 Derlemenin yüklenme şekli, tam zamanında (JıT) derlenmiş kodun, işlemdeki birden çok uygulama etki alanı tarafından paylaşılıp paylaşılamayacağını belirler.  
  
- Bir derleme etki alanı nötr olarak yüklenirse, aynı güvenlik izni kümesini paylaşan tüm uygulama etki alanları JıT ile derlenen aynı kodu paylaşabilir. Bu, uygulamanın gerektirdiği belleği azaltır.  
  
- Bir derleme etki alanı nötr olarak yüklenmediyse, uygulamasının yüklendiği her uygulama etki alanında JıT olarak derlenmesi ve yükleyicinin, uygulama etki alanları arasında iç kaynakları paylaşmamalıdır olması gerekir.  
  
 1 olarak ayarlandığında, COMPLUS_LoaderOptimization Environment bayrağı, çalışma zamanı konağını, SingleDomain olarak bilinen, etki alanı olmayan bağımsız şekilde tüm derlemeleri yüklemeye zorlar. SingleDomain, her zaman etki alanı nötr olarak yüklenen mscorlib dışında, hiçbir derlemeyi etki alanı nötr olarak yüklemez. Bu ayar, ana bilgisayar işlemde yalnızca tek bir uygulama çalıştırırken yaygın olarak kullanıldığından, tek etki alanı olarak adlandırılır.  
  
> [!CAUTION]
> COMPLUS_LoaderOptimization ortam bayrağı, tanılama ve test senaryolarında kullanılmak üzere tasarlanmıştır. Bayrağın açık olması ciddi yavaşlamaya ve bellek kullanımında artışa neden olabilir.  
  
### <a name="code-example"></a>Kod örneği

 Tüm derlemelerin yüklenmelerini zorlamak için, IISADMIN hizmeti için etki alanı nötr olarak, HKEY_LOCAL_MACHINE \System\currentcontrolset\services\ıısadmın anahtarındaki ortamın `COMPLUS_LoaderOptimization=1` çok dizeli değerine eklenerek elde edilebilir.  
  
```env  
Key = HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN  
Name = Environment  
Type = REG_MULTI_SZ  
Value (to append) = COMPLUS_LoaderOptimization=1  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AppDomain?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject?displayProperty=nameWithType>
- [Uygulama Etki Alanları ve Derlemelerle Programlama](index.md)
- [Uygulama Etki Alanlarını Kullanma](use.md)
