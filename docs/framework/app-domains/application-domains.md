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
ms.openlocfilehash: 811443dbd8e2483f7fc1b0f8c44afb4ebcd9efcf
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="application-domains"></a>Uygulama Etki Alanları
İşletim sistemleri ve çalışma zamanı ortamları tipik olarak bazı form uygulamalar arasında yalıtım sağlar. Örneğin, Windows uygulamalarını yalıtmak için işlemleri kullanır. Bu yalıtım bir uygulamada çalışan kodu ilgisiz, diğer uygulamalar olumsuz etkileyemez sağlamak gereklidir.  
  
 Uygulama etki alanları, güvenlik, güvenilirlik ve sürüm oluşturma ve yüklemeyi kaldırma derlemeler için bir yalıtım sınırı sağlar. Uygulama etki alanları genellikle bir uygulamayı çalıştırmadan önce ortak dil çalışma zamanı önyüklemesinden sorumlu çalışma zamanı konaklar tarafından oluşturulur.  
  
 Bu bölümdeki konular, belgelerin uygulama etki alanları arasında derlemeleri yalıtımı sağlamak için nasıl kullanılacağı açıklanmaktadır.  
  
 Bu genel bakışta aşağıdaki bölümleri içerir:  
  
-   [Uygulamaları Yalıtma avantajları](#benefits)  
  
-   [Başvuru](#reference)  
  
<a name="benefits"></a>   
## <a name="the-benefits-of-isolating-applications"></a>Uygulamaları Yalıtma avantajları  
 Tarihsel olarak, aynı bilgisayarda çalışan uygulamalarını yalıtmak için işlem sınırları kullanıldı. Her uygulama aynı bilgisayarda çalışan diğer uygulamalardan ayıran ayrı bir işlemde içine yüklenir.  
  
 Bellek adreslerini işlem göreli olduğundan uygulamaları yalıtılmış; başka bir işleminden geçirilen bir bellek işaretçisi herhangi anlamlı bir şekilde hedef işlemde kullanılamaz. Ayrıca, iki işlem arasında doğrudan çağrılar yapamazsınız. Bunun yerine, bir yöneltme düzeyini sağlamak proxy'leri kullanmanız gerekir.  
  
 Yönetilen kod (yönetici Doğrulamayı atla izni sürece) çalıştırabilmeniz için önce bir doğrulama işlemi geçirilmelidir. Doğrulama işlemi, kodu erişim geçersiz bellek adresleri veya içinde düzgün çalışması kapatmaya çalıştığı işlemin neden olabilecek başka bir eylemi gerçekleştirmek deneyebilirsiniz olup olmadığını belirler. Doğrulama testi geçirir kod tür kullanımı uyumlu olarak kabul edilir. Tür kullanımı uyumlu olarak kod doğrulamak için ortak dil çalışma zamanı olarak harika işlem sınırında bir çok düşük performans olarak yalıtım düzeyini sağlamak amacıyla sağlar.  
  
 Uygulama etki alanları ortak dil çalışma zamanı uygulamalar arasında yalıtım sağlamak için kullanabileceği işleme daha güvenli ve çok yönlü birimi sağlayın. Aynı ayrı işlemlerdeki ancak çapraz işlem çağrıları yapma veya işlemler arasında geçiş ek yükünü yansıtılmasını olmadan var yalıtım düzeyine sahip tek bir işlemde birkaç uygulama etki alanları çalıştırabilirsiniz. Tek bir işlem içinde birden çok uygulama önemli ölçüde çalıştırma yeteneğini sunucu ölçeklenebilirliğini artırır.  
  
 Uygulamaları Yalıtma da uygulama güvenliği için önemlidir. Örneğin, bir tek tarayıcı işlemde denetimleri birbirlerinin verilerine ve kaynaklarına erişemiyor şekilde birkaç Web uygulamalarından denetimleri çalıştırabilir.  
  
 Uygulama etki alanları tarafından sağlanan yalıtım aşağıdaki faydaları vardır:  
  
-   Bir uygulamadaki hataları diğer uygulamaları etkileyemez. Tür kullanımı uyumlu kod bellek hatalarına neden yapılamıyor çünkü uygulama etki alanları kullanarak bir etki alanında çalışan kodu işlem diğer uygulamalarda etkileyemez sağlar.  
  
-   Tek tek uygulamalar bütün işlem durdurmadan durdurulabilir. Uygulama etki alanları kullanarak, tek bir uygulama içinde çalışan kodu unload olanak sağlar.  
  
    > [!NOTE]
    >  Ayrı ayrı derlemeler veya türleri kaldıramıyor. Yalnızca tam etki alanı kaldırılmış olabilir.  
  
-   Bir uygulamada çalışan kodu doğrudan erişim kodu ya da başka bir uygulama kaynaklardan yükleyemezsiniz. Ortak dil çalışma zamanı, farklı uygulama etki alanlarında nesneleri arasında doğrudan çağrılar engelleyerek bu yalıtım zorlar. Etki alanları arasında geçirmek nesneler kopyalanan ya da proxy tarafından erişilebilir. Nesne kopyaladıysanız, nesne için yerel çağrıdır. Diğer bir deyişle, çağıran ve başvurulan nesne aynı uygulama etki alanındadır. Nesne bir proxy üzerinden erişilen, nesne çağrısı uzak olur. Bu durumda, çağıranın ve başvurulan nesne farklı uygulama etki alanlarında markalarıdır. Etki alanları arası çağrılar çağrıları iki makine arasında veya iki işlemler arasında aynı uzak çağrı altyapısını kullanır. Bu nedenle, başvurulan nesne için meta veriler JIT derlenmiş düzgün olmasını yöntem çağrısı izin vermek için her iki uygulama etki alanları için kullanılabilir olmalıdır. Çağıran etki çağrılan nesnesi için meta veri erişimi yoksa, derleme türünde bir özel durum ile başarısız olabilir **System.IO.FileNotFound**. Bkz: [uzak nesneleri](http://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58) daha fazla ayrıntı için. Nesneleri etki alanları arasında nasıl erişilebileceğini belirlemek için mekanizması nesne tarafından belirlenir. Daha fazla bilgi için bkz. <xref:System.MarshalByRefObject?displayProperty=nameWithType>.  
  
-   Kod davranışını içinde çalışan uygulama tarafından kapsamlıdır. Diğer bir deyişle, uygulama etki alanı uygulama sürüm ilkeleri, eriştiği herhangi bir uzak derlemeler ve etki alanına yüklenmiş derlemeleri yerleştireceğinizi hakkında bilgi konumu gibi yapılandırma ayarlarını sağlar.  
  
-   Kod için izinler kodu çalıştığı uygulama etki alanı tarafından denetlenebilir.  
  
  
## <a name="application-domains-and-assemblies"></a>Uygulama Etki Alanları ve Derlemeler  
 Bu konuda uygulama etki alanları ve derlemeler arasındaki ilişki açıklanmaktadır. Bir derlemenin içerdiği kodu yürütmeden önce derlemeyi bir uygulama etki alanına yüklemeniz gerekir. Tipik bir uygulamayı çalıştırmak, bir uygulama etki alanına birkaç derlemenin yüklenmesine neden olur.  
  
 Bir derlemenin yüklenme şekli, onun işlemdeki birden çok uygulama etki alanı ile paylaşılabilen anlık (JIT) derlenmiş kod olup olmadığını ve derlemenin işlemden kaldırılabilip kaldırılamayacağını belirler.  
  
-   Eğer bir derleme etki alanından bağımsız olarak yüklenirse, aynı güvenlik izni kümesine sahip olan tüm uygulama etki alanları aynı JIT olarak derlenmiş kodunu paylaşabilir ve bu da uygulamanın gerektirdiği belleği azaltır. Ancak, derleme işlemden asla kaldırılamaz.  
  
-   Eğer bir derleme etki alanından bağımsız olarak yüklenmezse, yüklendiği tüm uygulama etki alanlarında JIT olarak derlenmelidir. Ancak derleme, yüklü olduğu tüm uygulama etki alanları kaldırılarak işlemden kaldırılabilir.  
  
 Çalışma zamanı konak ortamı, çalışma zamanını bir işleme yüklerken derlemeleri etki alanından bağımsız olarak yükleyip yüklemeyeceğini belirler. Yönetilen uygulamalar için, <xref:System.LoaderOptimizationAttribute> özniteliğini işlem için giriş noktası metoduna uygulayın ve ilişkili <xref:System.LoaderOptimization> sabit listesinden bir değer belirtin. Ortak dil çalışma zamanı ana bilgisayar yönetilmeyen uygulamaları belirtmek için uygun bayrağı çağırdığınızda [CorBindToRuntimeEx işlevi](../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) yöntemi.  
  
 Etki alanından bağımsız derlemeleri yüklemek için üç seçenek vardır:  
  
- <xref:System.LoaderOptimization.SingleDomain?displayProperty=nameWithType>, her zaman etki alanından bağımsız olarak yüklenen Mscorlib dışındaki hiçbir derlemeyi etki alanından bağımsız olarak yüklemez. Ana bilgisayar işleminde yalnızca tek bir uygulama çalışırken sık kullanıldığı için bu ayar tek etki alanı adı verilir.

- <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType>, tüm derlemeleri etki alanından bağımsız yükler. İşlemde tamamı aynı kodu çalıştıran birden çok uygulama etki alanı olduğunda bu ayarı kullanın.

- <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, tanımlayıcı ada sahip olan derlemeleri, kendileri ve tüm bağımlılıkları genel bütünleştirilmiş kod önbelleğinde yüklü ise, etki alanından bağımsız olarak yükler. Diğer derlemeler yüklü oldukları her uygulama etki alanı için ayrı olarak yüklenip JIT olarak derlenirler ve bu nedenle işlemden kaldırılabilirler. Aynı işlemde birden çok uygulama çalıştırırken veya işlemden kaldırılması gereken birden çok uygulama etki alanı ve derleme tarafından paylaşılan bir derleme karışımına sahipseniz bu ayarı kullanın.
  
 JIT olarak derlenmiş kod, <xref:System.Reflection.Assembly.LoadFrom%2A> sınıfının <xref:System.Reflection.Assembly> yöntemi kullanarak load-from bağlamı içine yüklenen derlemeler için ya da <xref:System.Reflection.Assembly.Load%2A> yönteminin bayt dizilerini belirten aşırı yüklemeleri kullanılarak görüntülerden yüklenen derlemeler için paylaşılamaz.  
  
 Yerel kod kullanılarak derlenmiştir derlemeleri [Ngen.exe (yerel Görüntü Oluşturucu)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) oldukları süreç içine yüklenen ilk etki alanı Tarafsız yüklerse, uygulama etki alanları arasında paylaşılabilir.  
  
 Uygulama giriş noktasını içeren derleme için JIT olarak derlenmiş kod, yalnızca tüm bağımlılıkları paylaşılabiliyorsa paylaşılır.  
  
 Etki alanından bağımsız bir derleme JIT olarak birden çok kez derlenebilir. Örneğin, iki uygulama etki alanının güvenlik izni kümeleri farklıysa, aynı JIT olarak derlenmiş kodu paylaşamazlar. Ancak, JIT olarak derlenmiş derlemenin her kopyası, aynı izin kümesine sahip olan diğer uygulama etki alanlarıyla paylaşılabilir.  
  
 Derlemeleri etki alanından bağımsız olarak yükleyip yüklemeyeceğinize karar verdiğinizde, bellek kullanımı ve diğer performans etmenleri arasında bir takas yapmanız gerekir.  
  
-   Etki alanından bağımsız derlemeler için statik verilere ve yöntemlere olan erişim, derlemeleri yalıtmak gerektiği için daha yavaştır. Statik alanlardaki nesnelere olan başvuruların etki alanı sınırlarını geçmesini engellemek için derlemeye erişen tüm uygulama etki alanlarının, statik verinin ayrı kopyalarına sahip olması gerekir. Sonuç olarak, çalışma zamanı bir çağıranı statik veri veya yöntemin uygun kopyasına yönlendirmek için ek mantık içerir. Bu ek mantık, çağrıyı yavaşlatır.  
  
-   Derleme etki alanından bağımsız olarak yüklendiğinde, derlemenin tüm bağımlılıkları konumlandırılıp yüklenmelidir çünkü etki alanından bağımsız olarak yüklenemeyen bir bağımlılık, derlemenin etki alanından bağımsız olarak yüklenmesini engeller.  
  
## <a name="application-domains-and-threads"></a>Uygulama Etki Alanları ve İş Parçacıkları  
 Uygulama etki alanı güvenlik, sürüm, güvenilirlik ve yönetilen kodu kaldırılması için bir yalıtım sınırı oluşturur. Bir iş parçacığı kod yürütmek için ortak dil çalışma zamanı tarafından kullanılan işletim sistemi yapıdır. Çalışma zamanında, tüm yönetilen kod uygulama etki alanına yüklenir ve bir veya daha fazla yönetilen iş parçacığı tarafından çalıştırın.  
  
 Uygulama etki alanları ve iş parçacıkları arasında bire bir bağıntı değil. Birkaç iş parçacığı bir tek bir uygulama etki alanındaki herhangi bir zamanda çalıştırabilirsiniz ve belirli bir iş parçacığı tek bir uygulama etki alanı için sınırlı değildir. Diğer bir deyişle, iş parçacığı uygulama etki alanı sınırları arası boş; Yeni bir iş parçacığı her uygulama etki alanı için oluşturulmamış.  
  
 Belirli bir zamanda, her iş parçacığı bir uygulama etki alanında yürütür. Sıfır, bir veya birden çok iş parçacığı herhangi belirli uygulama etki alanında yürütülüyor. Çalışma zamanında hangi uygulama etki alanında çalışan hangi iş parçacığı izler. Etki alanı içinde bir iş parçacığı Yürütülüyor herhangi bir zamanda çağırarak bulabilir <xref:System.Threading.Thread.GetDomain%2A?displayProperty=nameWithType> yöntemi.  
  
### <a name="application-domains-and-cultures"></a>Uygulama etki alanları ve kültürler  
 Tarafından temsil edilen kültür bir <xref:System.Globalization.CultureInfo> nesnesi, iş parçacığı ile ilişkilidir. Kullanarak şu anda yürütülen iş parçacığı ile ilişkilendirilen kültür alabilirsiniz <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliği ve almak veya ayarlamak kullanarak şu anda yürütülen iş parçacığı ile ilişkilendirilen kültür <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği. İş parçacığı ile ilişkili kültürü kullanarak açıkça ayarlanmış <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği, devam iş parçacığı uygulama etki alanı sınırları kestiği zaman bu iş parçacığı ile ilişkilendirilecek. Aksi takdirde, herhangi bir zamanda iş parçacığı ile ilişkilendirilen kültür değeri olarak belirlenir <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> iş parçacığı Yürütülüyor uygulama etki alanındaki özelliğin:  
  
-   Özelliğinin değeri değilse `null`, özellik tarafından döndürülen iş parçacığı ile ilişkili kültürdür (ve bu nedenle tarafından döndürülen <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> ve <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özellikleri).  
  
-   Özelliğinin değeri ise `null`, geçerli sistem kültürü iş parçacığı ile ilişkilidir.  
  
## <a name="programming-with-application-domains"></a>Uygulama Etki Alanlarıyla Programlama  
 Uygulama etki alanları genellikle programlı olarak çalışma zamanı ana bilgisayarları tarafından oluşturulur ve değiştirilir. Ancak, bazen bir uygulama programı da uygulama etki alanları ile birlikte çalışmak isteyebilir. Örneğin, bir uygulama programı, tüm uygulamayı durdurmasına gerek kalmadan etki alanını (ve bileşeni) kaldırabilmek için bir etki alanına bir uygulama bileşeni yükleyebilir.  
  
 <xref:System.AppDomain> Uygulama etki alanları için programlama arabirimidir. Bu sınıf, etki alanları oluşturmak ve kaldırmak, etki alanlarında türlerin örneklerini oluşturmak ve uygulama etki alanı kaldırma gibi belirli bildirimlere kaydolmak için metotlar içerir. Aşağıdaki tabloda yaygın olarak kullanılan <xref:System.AppDomain> yöntemleri.  
  
|AppDomain Yöntemi|Açıklama|  
|----------------------|-----------------|  
|<xref:System.AppDomain.CreateDomain%2A>|Yeni bir uygulama etki alanı oluşturur. Bu yöntemin bir <xref:System.AppDomainSetup> nesnesi belirten bir aşırı yüklemesini kullanmanız önerilir. Bu; yeni bir etki alanının uygulama temel dizini veya uygulamanın kök dizini, etki alanı için yapılandırma dosyasının konumu ve ortak dil çalışma zamanının etki alanına yeni derlemeler yüklemek için kullanacağı arama yolu gibi özelliklerini ayarlamak için tercih edilen yöntemdir.|  
|<xref:System.AppDomain.ExecuteAssembly%2A> Ve <xref:System.AppDomain.ExecuteAssemblyByName%2A>|Uygulama etki alanındaki bir derlemeyi yürütür. Bu bir örnek yöntemi olduğundan, atıfta bulunduğunuz başka bir uygulama etki alanındaki kodu yürütmek için kullanılabilir.|  
|<xref:System.AppDomain.CreateInstanceAndUnwrap%2A>|Uygulama etki alanında belirtilen bir türün bir örneğini oluşturur ve bir proxy döndürür. Oluşturulan türü içeren derlemenin, bu derlemeyi çağıran derlemeye yüklenmesini engellemek için kullanın.|  
|<xref:System.AppDomain.Unload%2A>|Etki alanının düzgün bir şekilde kapatılmasını gerçekleştirir. Uygulama etki alanı, etki alanındaki tüm iş parçacıkları durmadan veya etki alanının dışında olmadan kaldırılmaz.|  
  
> [!NOTE]
>  Ortak dil çalışma zamanı, genel yöntemlerin serileştirilmesini desteklemediğinden, temsilciler kullanılarak diğer uygulama etki alanlarındaki genel yöntemler yürütülemez.  
  
 Ortak dil çalışma zamanı Ana Bilgisayarları Arabirimleri Bildirimi'nde açıklanan yönetilmeyen arabirimler de uygulama etki alanlarına erişim sağlar. Çalışma zamanı ana bilgisayarları, yönetilmeyen koddan arabirimler kullanarak bir işlem içinde uygulama etki alanları oluşturabilir veya onlara erişebilir.  
  
## <a name="complusloaderoptimization-environment-variable"></a>COMPLUS_LoaderOptimization Ortam Değişkeni  
 Yürütülebilir uygulamanın varsayılan yükleyicisi iyileştirme ilkesini ayarlar bir ortam değişkeni.  
  
### <a name="syntax"></a>Sözdizimi  
  
```  
COMPLUS_LoaderOptimization = 1  
```  
  
### <a name="remarks"></a>Açıklamalar  
 Tipik bir uygulama içerdikleri kod yürütülebilmesi birkaç derlemeleri uygulama etki alanına yükler.  
  
 Derleme yüklenmiş şekilde kendi tam zamanında (JIT) derlenmiş kod olup olmadığını belirler işlemde birden çok uygulama etki alanları tarafından paylaşılabilir.  
  
-   Bir derlemeyi yüklenen etki alanı neutral ise, aynı güvenlik verme kümesi paylaşan tüm uygulama etki alanları aynı JIT derlenmiş kod paylaşabilirsiniz. Bu uygulama tarafından gerekli bellek azaltır.  
  
-   Bir derlemeyi yüklenen etki alanı Tarafsız değilse, bu yüklendiği ve yükleyicisi uygulama etki alanları arasında iç kaynaklara paylaşmamalıdır her uygulama etki alanındaki JIT derlenmiş olmalıdır.  
  
 1 olarak ayarlandığında, çalışma zamanı ana bilgisayarı etki alanından bağımsız şekilde SingleDomain bilinen tüm derlemeleri yüklemeye COMPLUS_LoaderOptimization ortamı bayrak zorlar. SingleDomain hiçbir derlemeleri her zaman etki alanı Tarafsız yüklenen Mscorlib dışında etki alanı Tarafsız olarak yükler. Ana bilgisayar işleminde yalnızca tek bir uygulama çalışırken sık kullanıldığı için bu ayar tek etki alanı adı verilir.  
  
> [!CAUTION]
>  COMPLUS_LoaderOptimization ortam bayrağı tanı kullanılmak üzere tasarlanmış ve test senaryoları. Açık bayrağı sahip Ciddi konumlanır neden ve bellek kullanımını artırır.  
  
### <a name="code-example"></a>Kod Örneği  
 Yüklenmeyeceğini tüm derlemeler için IISADMİN olarak etki alanı Tarafsız zorlamak için hizmet eklenerek elde edilebilir `COMPLUS_LoaderOptimization=1` HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN anahtarında ortamı çok dizeli değer.  
  
```  
Key = HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN  
Name = Environment  
Type = REG_MULTI_SZ  
Value (to append) = COMPLUS_LoaderOptimization=1  
```  
  
<a name="reference"></a>   
## <a name="reference"></a>Başvuru  
 <xref:System.MarshalByRefObject?displayProperty=nameWithType>
