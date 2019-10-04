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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ce9d5f706a473d64e97fb02e0426060878d9c75
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834026"
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
  
- Bir uygulamada çalışan kod, başka bir uygulamadan koda veya kaynaklara doğrudan erişemez. Ortak dil çalışma zamanı, farklı uygulama etki alanlarındaki nesneler arasındaki doğrudan çağrıları önleyerek bu yalıtımı zorlar. Etki alanları arasında geçiş yapan nesneler, proxy tarafından kopyalanır veya erişilir. Nesne kopyalanırsa, nesnesine yapılan çağrı yereldir. Diğer bir deyişle, hem çağıran hem de başvurulan nesne aynı uygulama etki alanında olur. Nesnesine bir proxy üzerinden erişiliyorsa, nesnesine yapılan çağrı uzak olur. Bu durumda, çağıran ve başvurulan nesne farklı uygulama etki alanlarında. Çapraz etki alanı çağrıları, iki işlem arasındaki veya iki makine arasındaki çağrılarla aynı uzaktan çağrı altyapısını kullanır. Bu nedenle, başvurulan nesnenin meta verileri, yöntem çağrısının JıT olarak derlenmesine izin vermek için her iki uygulama etki alanı için de kullanılabilir olmalıdır. Çağıran etki alanının çağrılan nesnenin meta verilerine erişimi yoksa, derleme <xref:System.IO.FileNotFoundException> türünde bir özel durumla başarısız olabilir. Daha fazla bilgi için bkz. [uzak nesneler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)). Nesneleri etki alanları genelinde nasıl erişilebileceğini belirleme mekanizması nesne tarafından belirlenir. Daha fazla bilgi için bkz. <xref:System.MarshalByRefObject?displayProperty=nameWithType>.  
  
- Kodun davranışı, çalıştığı uygulamanın kapsamına alınır. Diğer bir deyişle, uygulama etki alanı, uygulama sürüm ilkeleri, eriştiği uzak derlemelerin konumu ve etki alanına yüklenen derlemelerin nerede bulunacağı hakkında bilgi gibi yapılandırma ayarları sağlar.  
  
- Koda verilen izinler, kodun çalıştığı uygulama etki alanı tarafından denetlenebilir.  
  
## <a name="application-domains-and-assemblies"></a>Uygulama etki alanları ve derlemeler

 Bu bölüm, uygulama etki alanları ve derlemeler arasındaki ilişkiyi açıklar. İçerdiği kodu yürütmeden önce bir derlemeyi uygulama etki alanına yüklemeniz gerekir. Tipik bir uygulamanın çalıştırılması, çeşitli derlemelerin bir uygulama etki alanına yüklenmesine neden olur.  
  
 Bir derlemenin yüklenme şekli, tam zamanında (JıT) derlenmiş kodun, işlemdeki birden çok uygulama etki alanı tarafından paylaşılıp paylaşılamayacağını ve derlemenin işlemden kaldırılabileceğini belirler.  
  
- Bir derleme etki alanı nötr olarak yüklenirse, aynı güvenlik izni kümesini paylaşan tüm uygulama etki alanları aynı JıT kodlu kodu paylaşabilir, bu da uygulamanın gerektirdiği belleği azaltır. Ancak, derleme işlemden hiçbir şekilde kaldırılamaz.  
  
- Bir derleme, etki alanına bağımsız yüklenmemişse, yüklendiği her uygulama etki alanında JıT olarak derlenmelidir. Ancak, derleme, yüklendiği tüm uygulama etki alanlarını kaldırarak işlemden kaldırılabilirler.  
  
 Çalışma zamanı ana bilgisayarı, çalışma zamanını bir işleme yüklediğinde, derlemelerin etki alanı nötr olarak yüklenip yüklenmeyeceğini belirler. Yönetilen uygulamalar için, <xref:System.LoaderOptimizationAttribute> özniteliğini işlem için giriş noktası yöntemine uygulayın ve ilişkili <xref:System.LoaderOptimization> numaralandırmasından bir değer belirtin. Ortak dil çalışma zamanını barındıran yönetilmeyen uygulamalar için [CorBindToRuntimeEx işlev](../unmanaged-api/hosting/corbindtoruntimeex-function.md) yöntemini çağırdığınızda uygun bayrağı belirtin.  
  
 Etki alanı bağımsız derlemeleri yüklemek için üç seçenek vardır:  
  
- <xref:System.LoaderOptimization.SingleDomain?displayProperty=nameWithType>, her zaman etki alanı nötr olarak yüklenen mscorlib dışında, hiçbir derlemeyi etki alanı nötr olarak yükler. Bu ayar, ana bilgisayar işlemde yalnızca tek bir uygulama çalıştırırken yaygın olarak kullanıldığından, tek etki alanı olarak adlandırılır.

- <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> tüm derlemeleri etki alanı nötr olarak yükler. İşlemde, hepsi aynı kodu çalıştıran birden çok uygulama etki alanı olduğunda bu ayarı kullanın.

- <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, ve tüm bağımlılıkları genel derleme önbelleğinde yüklüyse, tanımlayıcı adlı derlemeleri etki alanı nötr olarak yükler. Diğer derlemeler yüklendikleri her uygulama etki alanı için ayrı olarak yüklenir ve JıT olarak derlenir ve bu nedenle işlemden kaldırılabilirler. Aynı işlemde birden fazla uygulama çalıştırırken veya işlemden yüklemesi gereken birçok uygulama etki alanı ve derlemesi tarafından paylaşılan derlemelerin bir karışımını varsa bu ayarı kullanın.
  
 JıT olarak derlenen kod, <xref:System.Reflection.Assembly> sınıfının <xref:System.Reflection.Assembly.LoadFrom%2A> yöntemi kullanılarak veya bir bayt dizileri belirten <xref:System.Reflection.Assembly.Load%2A> yönteminin aşırı yüklemeleri kullanılarak görüntülerden yüklenen, Load-to----------from bağlamına yüklenen derlemeler için paylaştırılamaz.  
  
 [Ngen. exe (yerel görüntü Oluşturucu)](../tools/ngen-exe-native-image-generator.md) kullanılarak yerel koda derlenmiş derlemeler, bir işleme ilk kez yüklendiklerinde etki alanı nötr olarak yüklenirse, uygulama etki alanları arasında paylaşılabilir.  
  
 Uygulama giriş noktasını içeren derleme için JıT ile derlenen kod yalnızca tüm bağımlılıkları paylaşılırsa paylaşılır.  
  
 Bir etki alanı bağımsız derlemesi JıT olarak birden çok kez derlenebilir. Örneğin, iki uygulama etki alanının güvenlik izni kümesi farklıysa, aynı JıT kodlu kodu paylaşamaz. Ancak, JıT ile derlenen derlemenin her kopyası aynı izin kümesine sahip olan diğer uygulama etki alanlarıyla paylaşılabilir.  
  
 Derlemeleri etki alanı için bağımsız olarak yükleyip yükleyemeyeceğine karar verirken, bellek kullanımını azaltma ve diğer performans faktörleri arasında bir zorunluluğunu getirir yapmanız gerekir.  
  
- Statik verilere ve yöntemlere erişim, derlemeleri yalıtma gereksinimi nedeniyle, etki alanı nötr derlemeler için daha yavaştır. Derlemeye erişen her uygulama etki alanının statik verilerin ayrı bir kopyasına sahip olması gerekir ve statik alanlardaki nesnelere yapılan başvuruların etki alanı sınırlarının sınırlarını önler. Sonuç olarak, çalışma zamanı, çağrıyı statik verilerin veya metodun uygun kopyasına yönlendirmek için ek mantık içerir. Bu ek mantık çağrıyı yavaşlatır.  
  
- Bir derlemenin tüm bağımlılıkları, derleme etki alanı nötr olduğunda yerleştirilmelidir ve yüklenmelidir çünkü etki alanı nötr olarak yüklenemeyen bir bağımlılık, derlemenin etki alanından bağımsız olarak yüklenmesini önler.  
  
## <a name="application-domains-and-threads"></a>Uygulama etki alanları ve iş parçacıkları

 Uygulama etki alanı, yönetilen kodun güvenliği, sürümü oluşturma, güvenilirlik ve kaldırılması için bir yalıtım sınırı oluşturur. İş parçacığı, kodu yürütmek için ortak dil çalışma zamanı tarafından kullanılan işletim sistemi yapısıdır. Çalışma zamanında, tüm yönetilen kodlar bir uygulama etki alanına yüklenir ve bir veya daha fazla yönetilen iş parçacığı tarafından çalıştırılır.  
  
 Uygulama etki alanları ve iş parçacıkları arasında bire bir bağıntı yoktur. Birçok iş parçacığı, belirli bir zamanda tek bir uygulama etki alanında yürütebilir ve belirli bir iş parçacığı tek bir uygulama etki alanına göre sınırlandırmaz. Diğer bir deyişle, iş parçacıkları, uygulama etki alanı sınırları arasında ücretsizdir; her uygulama etki alanı için yeni bir iş parçacığı oluşturulmaz.  
  
 Belirli bir zamanda, her iş parçacığı bir uygulama etki alanında yürütülür. Sıfır, bir veya birden çok iş parçacığı belirli bir uygulama etki alanında Yürütülüyor olabilir. Çalışma zamanı, uygulama etki alanlarında hangi iş parçacıklarının çalıştığını izler. @No__t-0 yöntemini çağırarak bir iş parçacığının yürütüldüğü etki alanını dilediğiniz zaman bulabilirsiniz.

### <a name="application-domains-and-cultures"></a>Uygulama etki alanları ve kültürleri

 @No__t-0 nesnesiyle temsil edilen kültür, iş parçacıklarıyla ilişkilendirilir. @No__t-0 özelliğini kullanarak şu anda yürütülmekte olan iş parçacığıyla ilişkili kültürü alabilir ve <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliğini kullanarak şu anda yürütülmekte olan iş parçacığıyla ilişkilendirilmiş kültürü alabilir veya ayarlayabilirsiniz. Bir iş parçacığı ile ilişkili kültür <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği kullanılarak açıkça ayarlandıysa, iş parçacığı uygulama etki alanı sınırlarını aştığında bu iş parçacığıyla ilişkilendirilmeye devam eder. Aksi takdirde, belirli bir zamanda iş parçacığı ile ilişkili kültür, iş parçacığının yürütüldüğü uygulama etki alanındaki <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> özelliğinin değeri tarafından belirlenir:  
  
- Özelliğin değeri `null` değilse, özelliği tarafından döndürülen kültür iş parçacığıyla ilişkilendirilir (ve bu nedenle <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> ve <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özellikleri tarafından döndürülür).  
  
- Özelliğin değeri `null` ise, geçerli sistem kültürü iş parçacığıyla ilişkilendirilir.  
  
## <a name="programming-with-application-domains"></a>Uygulama etki alanlarıyla programlama

 Uygulama etki alanları genellikle çalışma zamanı konakları tarafından programlı olarak oluşturulur ve işlenir. Ancak, bazen bir uygulama programı da uygulama etki alanlarıyla çalışmak isteyebilir. Örneğin, bir uygulama programı uygulamanın tamamını durdurmak zorunda kalmadan etki alanını (ve bileşeni) kaldırabilmek için bir etki alanına uygulama bileşeni yükleyebilir.  
  
 @No__t-0, uygulama etki alanlarına yönelik programlama arabirimidir. Bu sınıf etki alanlarını oluşturma ve kaldırma, etki alanlarında türlerin örneklerini oluşturma ve uygulama etki alanı kaldırma gibi çeşitli bildirimlere kaydolma yöntemlerini içerir. Aşağıdaki tabloda, yaygın olarak kullanılan <xref:System.AppDomain> yöntemleri listelenmiştir.  
  
|AppDomain yöntemi|Açıklama|  
|----------------------|-----------------|  
|<xref:System.AppDomain.CreateDomain%2A>|Yeni bir uygulama etki alanı oluşturur. Bu yöntemin <xref:System.AppDomainSetup> nesnesini belirten bir aşırı yüklemesini kullanmanız önerilir. Bu, uygulama temeli veya uygulama için kök dizin gibi yeni bir etki alanının özelliklerini ayarlamak için tercih edilen yoldur; etki alanının yapılandırma dosyasının konumu; ve ortak dil çalışma zamanının, etki alanına derlemeleri yüklemek için kullanacağı arama yolu.|  
|<xref:System.AppDomain.ExecuteAssembly%2A> ve <xref:System.AppDomain.ExecuteAssemblyByName%2A>|Uygulama etki alanında bir derlemeyi yürütür. Bu bir örnek yöntemidir. bu nedenle, bir başvuruya sahip olduğunuz başka bir uygulama etki alanındaki kodu yürütmek için kullanılabilir.|  
|<xref:System.AppDomain.CreateInstanceAndUnwrap%2A>|Uygulama etki alanında belirtilen türde bir örnek oluşturur ve bir proxy döndürür. Oluşturulan türü içeren derlemenin çağıran derlemeye yüklenmesini önlemek için bu yöntemi kullanın.|  
|<xref:System.AppDomain.Unload%2A>|Etki alanının düzgün bir şekilde kapatılmasını gerçekleştirir. Etki alanında çalışan tüm iş parçacıkları durdurulmadığından veya artık etki alanında bulunmadığından, uygulama etki alanı kaldırılmıyor.|  
  
> [!NOTE]
> Ortak dil çalışma zamanı, genel yöntemlerin serileştirmesini desteklemez, bu nedenle temsilciler diğer uygulama etki alanlarında genel yöntemleri yürütmek için kullanılamaz.  
  
 Ortak dil çalışma zamanı barındırma arabirimleri belirtiminde açıklanan yönetilmeyen arabirimler, uygulama etki alanlarına da erişim sağlar. Çalışma zamanı Konakları yönetilmeyen koddan arabirimler kullanarak bir işlem içinde uygulama etki alanları oluşturabilir ve bu verilere erişim elde edebilir.  
  
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

 Tüm derlemelerin yüklenmelerini zorlamak için, HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN anahtarındaki ortamın çok dizeli değerine `COMPLUS_LoaderOptimization=1` eklenerek, IISADMIN hizmeti için etki alanı için bağımsız olarak.  
  
```env  
Key = HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN  
Name = Environment  
Type = REG_MULTI_SZ  
Value (to append) = COMPLUS_LoaderOptimization=1  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AppDomain?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject?displayProperty=nameWithType>
- [Uygulama etki alanları ve Derlemeleriyle programlama](index.md)
- [Uygulama etki alanlarını kullanma](use.md)
