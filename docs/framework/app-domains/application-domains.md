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

İşletim sistemleri ve çalışma zamanı ortamları genellikle uygulamalar arasında bir tür yalıtım sağlar. Örneğin, Windows uygulamaları yalıtmak için işlemleri kullanır. Bu yalıtım, bir uygulamada çalışan kodun diğer ilgisiz uygulamaları olumsuz etkilemeyeceğini sağlamak için gereklidir.  
  
 Uygulama etki alanları, güvenlik, güvenilirlik ve sürüm oluşturma ve derlemeleri boşaltma için bir yalıtım sınırı sağlar. Uygulama etki alanları genellikle, bir uygulama çalıştırılmadan önce ortak dil çalışma süresini önyüklemeden sorumlu olan çalışma zamanı ana bilgisayarları tarafından oluşturulur.  
  
## <a name="the-benefits-of-isolating-applications"></a>Uygulamaları yalıtmanın yararları

 Tarihsel olarak, işlem sınırları aynı bilgisayarda çalışan uygulamaları yalıtmak için kullanılmıştır. Her uygulama, uygulamayı aynı bilgisayarda çalışan diğer uygulamalardan yalıtan ayrı bir işleme yüklenir.  
  
 Bellek adresleri işlem göreli olduğundan uygulamalar yalıtılır; bir işlemden diğerine geçirilen bir bellek işaretçisi hedef işlemde anlamlı bir şekilde kullanılamaz. Ayrıca, iki işlem arasında doğrudan arama yapamazsınız. Bunun yerine, bir yönlendirme düzeyi sağlayan yakınlıklar kullanmanız gerekir.  
  
 Yönetilen kodun çalıştırılabilmek için bir doğrulama işleminden geçirilmesi gerekir (yönetici doğrulamayı atlamak için izin vermemişse). Doğrulama işlemi, kodun geçersiz bellek adreslerine erişmeye çalışıp çalışamayacağını veya çalıştığı işlemin düzgün çalışmaması için başka bir eylem gerçekleştirip gerçekleştiremeyeceğini belirler. Doğrulama testini geçen kodun tür güvenli olduğu söylenir. Kodu tür güvenli olarak doğrulama yeteneği, ortak dil çalışma zamanının çok daha düşük bir performans maliyetiyle işlem sınırı kadar büyük bir yalıtım düzeyi sağlamasını sağlar.  
  
 Uygulama etki alanları, ortak dil çalışma süresinin uygulamalar arasında yalıtım sağlamak için kullanabileceği daha güvenli ve çok yönlü bir işlem birimi sağlar. Birden çok uygulama etki alanını, ayrı işlemlerde var olacak aynı yalıtım düzeyine sahip, ancak çapraz işlem çağrıları yapma veya işlemler arasında geçiş yapma ek ek yükü ne gerektirmeden çalıştırabilirsiniz. Tek bir işlem içinde birden çok uygulama çalıştırma yeteneği sunucu ölçeklenebilirliğini önemli ölçüde artırır.  
  
 Uygulamaları yalıtma, uygulama güvenliği için de önemlidir. Örneğin, denetimlerin birbirinin verilerine ve kaynaklarına erişemeyeceği şekilde tek bir tarayıcı işleminde birden çok Web uygulamasından gelen denetimleri çalıştırabilirsiniz.  
  
 Uygulama etki alanları tarafından sağlanan yalıtım aşağıdaki avantajlara sahiptir:  
  
- Bir uygulamadaki hatalar diğer uygulamaları etkileyemez. Tür güvenli kod bellek hatalarına neden olamayacağından, uygulama etki alanlarını kullanmak, bir etki alanında çalışan kodun işlemdeki diğer uygulamaları etkilememesini sağlar.  
  
- Tek tek uygulamalar tüm işlem durdurulmadan durdurulabilir. Uygulama etki alanlarını kullanmak, tek bir uygulamada çalışan kodu boşaltmanızı sağlar.  
  
    > [!NOTE]
    > Tek tek derlemeleri veya türleri boşaltamazsınız. Yalnızca tam bir etki alanı boşaltılabilir.  
  
- Bir uygulamada çalışan kod, başka bir uygulamadan koda veya kaynaklara doğrudan erişemez. Ortak dil çalışma zamanı, farklı uygulama etki alanlarındaki nesneler arasında doğrudan çağrıları engelleyerek bu yalıtımı zorlar. Etki alanları arasında geçen nesneler kopyalanır veya proxy tarafından erişilir. Nesne kopyalanırsa, nesneye yapılan çağrı yereldir. Diğer bir deyişle, hem arayan hem de başvurulan nesne aynı uygulama etki alanındadır. Nesneye bir proxy üzerinden erişilirse, nesneye yapılan çağrı uzaktır. Bu durumda, arayan ve başvurulan nesne farklı uygulama etki alanlarındadır. Etki alanları arası aramalar, iki işlem arasındaki veya iki makine arasındaki aramalarla aynı uzak çağrı altyapısını kullanır. Bu nedenle, başvurulan nesnenin meta verilerinin, yöntem çağrısının JIT tarafından düzgün bir şekilde derlenmesine izin vermek için her iki uygulama etki alanı için de kullanılabilir olması gerekir. Çağrılanan nesne için meta verilere erişim arama etki alanı yoksa, derleme türü <xref:System.IO.FileNotFoundException>dışında başarısız olabilir. Daha fazla bilgi için [Uzak Nesneler'e](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))bakın. Nesnelerin etki alanları arasında nasıl erişileceğini belirleme mekanizması nesne tarafından belirlenir. Daha fazla bilgi için bkz. <xref:System.MarshalByRefObject?displayProperty=nameWithType>.  
  
- Kodun davranışı, çalıştığı uygulama tarafından kapsamlıdır. Başka bir deyişle, uygulama etki alanı, uygulama sürümü ilkeleri, eriştiği uzak derlemelerin konumu ve etki alanına yüklenen derlemelerin nerede bulunacağı hakkında bilgi gibi yapılandırma ayarları sağlar.  
  
- Koda verilen izinler, kodun çalıştırıldığı uygulama etki alanı tarafından denetlenebilir.  
  
## <a name="application-domains-and-assemblies"></a>Uygulama Etki Alanları ve derlemeler

 Bu bölümde, uygulama etki alanları ve derlemeler arasındaki ilişki açıklanmaktadır. Bir derlemenin içerdiği kodu yürütmeden önce derlemeyi bir uygulama etki alanına yüklemeniz gerekir. Tipik bir uygulamayı çalıştırmak, bir uygulama etki alanına birkaç derlemenin yüklenmesine neden olur.  
  
 Bir derlemenin yüklenme şekli, onun işlemdeki birden çok uygulama etki alanı ile paylaşılabilen anlık (JIT) derlenmiş kod olup olmadığını ve derlemenin işlemden kaldırılabilip kaldırılamayacağını belirler.  
  
- Eğer bir derleme etki alanından bağımsız olarak yüklenirse, aynı güvenlik izni kümesine sahip olan tüm uygulama etki alanları aynı JIT olarak derlenmiş kodunu paylaşabilir ve bu da uygulamanın gerektirdiği belleği azaltır. Ancak, derleme işlemden asla kaldırılamaz.  
  
- Eğer bir derleme etki alanından bağımsız olarak yüklenmezse, yüklendiği tüm uygulama etki alanlarında JIT olarak derlenmelidir. Ancak derleme, yüklü olduğu tüm uygulama etki alanları kaldırılarak işlemden kaldırılabilir.  
  
 Çalışma zamanı konak ortamı, çalışma zamanını bir işleme yüklerken derlemeleri etki alanından bağımsız olarak yükleyip yüklemeyeceğini belirler. Yönetilen uygulamalar için, <xref:System.LoaderOptimizationAttribute> özniteliğini işlem için giriş noktası metoduna uygulayın ve ilişkili <xref:System.LoaderOptimization> sabit listesinden bir değer belirtin. Ortak dil çalışma zamanını barındıran yönetilmeyen uygulamalar için [CorBindToRuntimeEx İşlev](../unmanaged-api/hosting/corbindtoruntimeex-function.md) yöntemini aradiğinizde uygun bayrağı belirtin.  
  
 Etki alanından bağımsız derlemeleri yüklemek için üç seçenek vardır:  
  
- <xref:System.LoaderOptimization.SingleDomain?displayProperty=nameWithType>, her zaman etki alanından bağımsız olarak yüklenen Mscorlib dışındaki hiçbir derlemeyi etki alanından bağımsız olarak yüklemez. Ana bilgisayar işlemde yalnızca tek bir uygulama çalışırken yaygın olarak kullanıldığından, bu ayarı tek etki alanı olarak adlandırılır.

- <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType>, tüm derlemeleri etki alanından bağımsız yükler. İşlemde tamamı aynı kodu çalıştıran birden çok uygulama etki alanı olduğunda bu ayarı kullanın.

- <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, tanımlayıcı ada sahip olan derlemeleri, kendileri ve tüm bağımlılıkları genel bütünleştirilmiş kod önbelleğinde yüklü ise, etki alanından bağımsız olarak yükler. Diğer derlemeler yüklü oldukları her uygulama etki alanı için ayrı olarak yüklenip JIT olarak derlenirler ve bu nedenle işlemden kaldırılabilirler. Aynı işlemde birden çok uygulama çalıştırırken veya işlemden kaldırılması gereken birden çok uygulama etki alanı ve derleme tarafından paylaşılan bir derleme karışımına sahipseniz bu ayarı kullanın.
  
 JIT olarak derlenmiş kod, <xref:System.Reflection.Assembly.LoadFrom%2A> sınıfının <xref:System.Reflection.Assembly> yöntemi kullanarak load-from bağlamı içine yüklenen derlemeler için ya da <xref:System.Reflection.Assembly.Load%2A> yönteminin bayt dizilerini belirten aşırı yüklemeleri kullanılarak görüntülerden yüklenen derlemeler için paylaşılamaz.  
  
 [Ngen.exe (Yerel Görüntü Üreteci)](../tools/ngen-exe-native-image-generator.md) kullanılarak yerel koda derlenen derlemeler, bir işleme ilk yüklendiğinde etki alanı tarafsız olarak yüklenirlerse uygulama etki alanları arasında paylaşılabilir.  
  
 Uygulama giriş noktasını içeren derleme için JIT olarak derlenmiş kod, yalnızca tüm bağımlılıkları paylaşılabiliyorsa paylaşılır.  
  
 Etki alanından bağımsız bir derleme JIT olarak birden çok kez derlenebilir. Örneğin, iki uygulama etki alanının güvenlik izni kümeleri farklıysa, aynı JIT olarak derlenmiş kodu paylaşamazlar. Ancak, JIT olarak derlenmiş derlemenin her kopyası, aynı izin kümesine sahip olan diğer uygulama etki alanlarıyla paylaşılabilir.  
  
 Derlemeleri etki alanından bağımsız olarak yükleyip yüklemeyeceğinize karar verdiğinizde, bellek kullanımı ve diğer performans etmenleri arasında bir takas yapmanız gerekir.  
  
- Etki alanından bağımsız derlemeler için statik verilere ve yöntemlere olan erişim, derlemeleri yalıtmak gerektiği için daha yavaştır. Statik alanlardaki nesnelere olan başvuruların etki alanı sınırlarını geçmesini engellemek için derlemeye erişen tüm uygulama etki alanlarının, statik verinin ayrı kopyalarına sahip olması gerekir. Sonuç olarak, çalışma zamanı bir çağıranı statik veri veya yöntemin uygun kopyasına yönlendirmek için ek mantık içerir. Bu ek mantık, çağrıyı yavaşlatır.  
  
- Derleme etki alanından bağımsız olarak yüklendiğinde, derlemenin tüm bağımlılıkları konumlandırılıp yüklenmelidir çünkü etki alanından bağımsız olarak yüklenemeyen bir bağımlılık, derlemenin etki alanından bağımsız olarak yüklenmesini engeller.  
  
## <a name="application-domains-and-threads"></a>Uygulama etki alanları ve iş parçacıkları

 Uygulama etki alanı, yönetilen kodun güvenliği, sürümlenmesi, güvenilirliği ve boşaltılması için bir yalıtım sınırı oluşturur. İş parçacığı, kodu yürütmek için ortak dil çalışma zamanı tarafından kullanılan işletim sistemi yapısıdır. Çalışma zamanında, yönetilen tüm kod bir uygulama etki alanına yüklenir ve bir veya daha fazla yönetilen iş parçacığı tarafından çalıştırılır.  
  
 Uygulama etki alanları ve iş parçacıkları arasında bire bir ilişki yoktur. Belirli bir iş parçacığı herhangi bir zamanda tek bir uygulama etki alanında yürütülebilir ve belirli bir iş parçacığı tek bir uygulama etki alanı ile sınırlı değildir. Diğer bir diğer nokta, iş parçacıkları uygulama etki alanı sınırlarını geçmekte serbesttir; her uygulama etki alanı için yeni bir iş parçacığı oluşturulmaz.  
  
 Herhangi bir zamanda, her iş parçacığı bir uygulama etki alanında yürütülür. Sıfır, bir veya birden çok iş parçacığı belirli bir uygulama etki alanında yürütülebilir. Çalışma zamanı, hangi iş parçacıklarının hangi uygulama etki alanlarında çalıştığını izler. <xref:System.Threading.Thread.GetDomain%2A?displayProperty=nameWithType> Yöntemi arayarak iş parçacığının herhangi bir zamanda yürütüldettiği etki alanını bulabilirsiniz.

### <a name="application-domains-and-cultures"></a>Uygulama alanları ve kültürleri

 Bir <xref:System.Globalization.CultureInfo> nesne tarafından temsil edilen kültür, iş parçacıklarıyla ilişkilidir. Özelliği kullanarak şu anda çalıştırılabilen iş parçacığıyla ilişkili kültürü alabilir ve <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği kullanarak şu anda çalıştırılabilen iş parçacığıyla ilişkili kültürü alabilirsiniz veya ayarlayabilirsiniz. İş parçacığı ile ilişkili kültür <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği kullanılarak açıkça ayarlanmışsa, iş parçacığı uygulama etki alanı sınırlarını geçtiğinde bu iş parçacığı ile ilişkili olmaya devam eder. Aksi takdirde, herhangi bir zamanda iş parçacığı ile ilişkili kültür <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> iş parçacığı yürütülderken uygulama etki alanında özelliğin değeri tarafından belirlenir:  
  
- Özelliğin değeri değilse, `null`özellik tarafından döndürülen kültür iş parçacığıyla ilişkilidir (ve bu <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> nedenle ve özellikleri tarafından döndürülür).  
  
- Özelliğin değeri ise, `null`geçerli sistem kültürü iş parçacığı ile ilişkilidir.  
  
## <a name="programming-with-application-domains"></a>Uygulama etki alanları yla programlama

 Uygulama etki alanları genellikle programlı olarak çalışma zamanı ana bilgisayarları tarafından oluşturulur ve değiştirilir. Ancak, bazen bir uygulama programı da uygulama etki alanları ile birlikte çalışmak isteyebilir. Örneğin, bir uygulama programı, tüm uygulamayı durdurmasına gerek kalmadan etki alanını (ve bileşeni) kaldırabilmek için bir etki alanına bir uygulama bileşeni yükleyebilir.  
  
 Uygulama <xref:System.AppDomain> etki alanları için programlı arabirimidir. Bu sınıf, etki alanları oluşturmak ve kaldırmak, etki alanlarında türlerin örneklerini oluşturmak ve uygulama etki alanı kaldırma gibi belirli bildirimlere kaydolmak için metotlar içerir. Aşağıdaki tabloda yaygın <xref:System.AppDomain> olarak kullanılan yöntemler listelenilmiştir.  
  
|AppDomain Yöntemi|Açıklama|  
|----------------------|-----------------|  
|<xref:System.AppDomain.CreateDomain%2A>|Yeni bir uygulama etki alanı oluşturur. Bu yöntemin bir <xref:System.AppDomainSetup> nesnesi belirten bir aşırı yüklemesini kullanmanız önerilir. Bu; yeni bir etki alanının uygulama temel dizini veya uygulamanın kök dizini, etki alanı için yapılandırma dosyasının konumu ve ortak dil çalışma zamanının etki alanına yeni derlemeler yüklemek için kullanacağı arama yolu gibi özelliklerini ayarlamak için tercih edilen yöntemdir.|  
|<xref:System.AppDomain.ExecuteAssembly%2A> ve <xref:System.AppDomain.ExecuteAssemblyByName%2A>|Uygulama etki alanındaki bir derlemeyi yürütür. Bu bir örnek yöntemi olduğundan, atıfta bulunduğunuz başka bir uygulama etki alanındaki kodu yürütmek için kullanılabilir.|  
|<xref:System.AppDomain.CreateInstanceAndUnwrap%2A>|Uygulama etki alanında belirtilen bir türün bir örneğini oluşturur ve bir proxy döndürür. Oluşturulan türü içeren derlemenin, bu derlemeyi çağıran derlemeye yüklenmesini engellemek için kullanın.|  
|<xref:System.AppDomain.Unload%2A>|Etki alanının düzgün bir şekilde kapatılmasını gerçekleştirir. Uygulama etki alanı, etki alanındaki tüm iş parçacıkları durmadan veya etki alanının dışında olmadan kaldırılmaz.|  
  
> [!NOTE]
> Ortak dil çalışma zamanı, genel yöntemlerin serileştirilmesini desteklemediğinden, temsilciler kullanılarak diğer uygulama etki alanlarındaki genel yöntemler yürütülemez.  
  
 Ortak dil çalışma zamanı Ana Bilgisayarları Arabirimleri Bildirimi'nde açıklanan yönetilmeyen arabirimler de uygulama etki alanlarına erişim sağlar. Çalışma zamanı ana bilgisayarları, yönetilmeyen koddan arabirimler kullanarak bir işlem içinde uygulama etki alanları oluşturabilir veya onlara erişebilir.  
  
## <a name="the-complus_loaderoptimization-environment-variable"></a>COMPLUS_LoaderOptimization ortamı değişkeni

 Yürütülebilir bir uygulamanın varsayılan yükleyici optimizasyon ilkesini ayarlayan bir ortam değişkeni.  
  
### <a name="syntax"></a>Sözdizimi  
  
```env  
COMPLUS_LoaderOptimization = 1  
```  
  
### <a name="remarks"></a>Açıklamalar

 Tipik bir uygulama, içerdikleri kod yürütülmeden önce birkaç derlemeyi bir uygulama etki alanına yükler.  
  
 Derlemenin yüklenme şekli, tam zamanında (JIT) derlenmiş kodunun işlemdeki birden çok uygulama etki alanı tarafından paylaşılıp paylaşılamayacağını belirler.  
  
- Bir derleme etki alanı nötr yüklenirse, aynı güvenlik hibe kümesini paylaşan tüm uygulama etki alanları aynı JIT tarafından derlenen kodu paylaşabilir. Bu, uygulamanın gerektirdiği belleği azaltır.  
  
- Bir derleme etki alanı nötr yüklenmezse, yüklendiği her uygulama etki alanında JIT derlenmiş olmalıdır ve yükleyici uygulama etki alanları arasında iç kaynakları paylaşmamalıdır.  
  
 COMPLUS_LoaderOptimization ortamı bayrağı 1 olarak ayarlandığında, çalışma zamanı ana bilgisayarını tüm derlemeleri Tek Etki Alanı olarak bilinen etki alanı tarafsız olmayan bir şekilde yüklemeye zorlar. SingleDomain, her zaman etki alanı nötr olarak yüklenen Mscorlib dışında hiçbir derlemeyi etki alanı nötr olarak yüklemez. Ana bilgisayar işlemde yalnızca tek bir uygulama çalışırken yaygın olarak kullanıldığından, bu ayarı tek etki alanı olarak adlandırılır.  
  
> [!CAUTION]
> COMPLUS_LoaderOptimization ortam bayrağı tanılama ve test senaryolarında kullanılmak üzere tasarlanmıştır. Bayrağın açık olması, bellek kullanımının ciddi şekilde yavaşlamaya ve artmasına neden olabilir.  
  
### <a name="code-example"></a>Kod örneği

 Tüm derlemeleri IISADMIN hizmeti için etki alanı nötr olarak yüklenmemeye `COMPLUS_LoaderOptimization=1` zorlamak için, HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN anahtarında Ortamın Çok String Değeri'ne eklenerek elde edilebilir.  
  
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
