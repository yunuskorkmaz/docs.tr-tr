---
title: Masaüstü Uygulamaları için Uydu Derlemeleri Oluşturma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- public keys, obtaining
- satellite assemblies
- assemblies [.NET Framework], signing
- application resources, deploying
- Al.exe
- GAC (global assembly cache), satellite assemblies
- Assembly Linker
- directory locations for satellite assemblies
- global assembly cache, satellite assemblies
- packaging application resources
- compiling satellite assemblies
- re-signing assemblies
ms.assetid: 8d5c6044-2919-41d2-8321-274706b295ac
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2f75da3332c8172a6a888e6f40c66383866799ea
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a>Masaüstü Uygulamaları için Uydu Derlemeleri Oluşturma
Kaynak dosyaları yerelleştirilmiş uygulamalarda merkezi bir rol oynar. Bunlar, bir uygulama kullanıcının kendi dil ve kültür dizeleri, resimleri ve diğer verileri görüntülemek ve kullanıcının kendi dilini veya kültür için kaynaklar kullanılamıyorsa alternatif veri sağlamak için etkinleştirin. .NET Framework bulun ve yerelleştirilmiş kaynaklar almak için bir hub ve bağlı bileşen modeli kullanır. Hub yerelleştirilemeyen yürütülebilir kod ve bağımsız olarak adlandırılan tek bir kültür için kaynakları içeren ana derlemedir veya varsayılan kültür. Geri dönüş kültürü uygulama için varsayılan kültürdür; hiçbir yerelleştirilmiş kaynaklar kullanılabilir olduğunda kullanılır. Kullandığınız <xref:System.Resources.NeutralResourcesLanguageAttribute> uygulamanın varsayılan kültürü kültürünü atamak özniteliği. Her bağlı bileşen tek bir yerelleştirilmiş kültür için kaynakları içerir, ancak herhangi bir kod içermiyor bir uydu derleme bağlanır. Uydu derlemeleri ana derleme parçası olmadığından, kolayca güncelleştirme veya uygulama için ana derleme değiştirmeden belirli bir kültür karşılık kaynakları değiştirin.  
  
> [!NOTE]
>  Bir uygulamanın varsayılan kültürü kaynakları da bir uydu derlemede depolanabilir. Bunu yapmak için Ata <xref:System.Resources.NeutralResourcesLanguageAttribute> değerini özniteliği <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>.  
  
## <a name="satellite-assembly-name-and-location"></a>Uydu derleme adı ve konumu  
 Hub ve bağlı bileşen modeli, böylece bunlar kolayca bulunan ve kullanılabilecek kaynaklar belirli konumlara yerleştirebilir gerektirir. Derleme ve ad kaynakları beklendiği gibi yapmak veya bunları doğru konumlara yerleştirmeyin, ortak dil çalışma zamanı bunları bulmak mümkün olmaz ve varsayılan kültürü kaynakları yerine kullanır. .NET Framework kaynağı tarafından temsil edilen Yöneticisi bir <xref:System.Resources.ResourceManager> nesnesi, otomatik olarak yerelleştirilmiş kaynaklara erişmek için kullanılır. Kaynak Yöneticisi için şunlar gerekir:  
  
-   Belirli bir kültür için tüm kaynakları tek bir uydu derlemesi içermelidir. Diğer bir deyişle, bir tek ikili kaynaklar dosyasına birden çok .txt veya .resx dosyaları derlemeniz gerekir.  
  
-   Bu kültürün kaynaklarının depolar her yerelleştirilmiş kültür için uygulama dizinindeki ayrı bir alt dizin olmalıdır. Alt dizinin adı kültür adı ile aynı olması gerekir. Alternatif olarak, genel derleme önbelleğinde uydu derlemelerini depolayabilirsiniz. Bu durumda, derleme tanımlayıcı adı kültür bilgilerini bileşeninin kültürü belirtmeniz gerekir. (Bkz [yükleme uydu derlemeleri Genel Derleme Önbelleği'ndeki](#SN) bu konunun ilerleyen bölümlerinde.)  
  
    > [!NOTE]
    >  Uygulamanızı subcultures kaynakları içeriyorsa, her alt uygulama dizini altındaki ayrı bir alt dizin yerleştirin. Subcultures kendi ana kültürün dizini altındaki dizinlerindeki yerleştirmeyin.  
  
-   Uydu derlemesi uygulama adıyla aynı olmalıdır ve dosya adı uzantısını kullanmalıdır ". resources.dll". Örneğin, bir uygulama Example.exe olarak adlandırılmışsa, her uydu derlemenin adını Example.resources.dll olmalıdır. Uydu derleme adı, kaynak dosyaları kültürünü göstermez unutmayın. Ancak, uydu derlemesi kültür belirtmek bir dizinde görünür.  
  
-   Uydu derlemesi kültürle ilgili bilgileri derlemenin meta verilerde eklenmesi gerekir. Kültür adı uydu derlemenin meta verilerini depolamak için belirttiğiniz `/culture` seçeneğini kullandığınızda [derleme bağlayıcı](../../../docs/framework/tools/al-exe-assembly-linker.md) kaynakları uydu derlemede katıştırmak için.  
  
 İçinde yüklemiyorsanız uygulamaları için bir örnek dizin yapısını ve konum gereksinimleri aşağıda gösterilmiştir [genel derleme önbelleği](../../../docs/framework/app-domains/gac.md). .Txt ve .resources uzantıları öğeleriyle son uygulama ile birlikte değil. Bu, son uydu kaynak derlemelerini oluşturmak için kullanılan ara kaynak dosyalarıdır. Bu örnekte, .resx dosyaları .txt dosyaları için alternatif. Daha fazla bilgi için bkz: [paketleme ve dağıtma kaynakları](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).  
  
 ![Uydu derlemeleri](../../../docs/framework/resources/media/satelliteassemblydir.gif "satelliteassemblydir")  
Uydu derleme dizini  
  
## <a name="compiling-satellite-assemblies"></a>Uydu derlemelerini derleme  
 Kullandığınız [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) metin veya ikili .resources dosyaları için kaynakları içeren XML (.resx) dosyaları derlemek için. Daha sonra [derleme bağlayıcı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) .resources dosyaları uydu derlemeye derlemesi için. Al.exe bir derleme belirttiğiniz .resources dosyaları oluşturur. Uydu derlemeleri yalnızca kaynakları içerebilir; Bunlar yürütülebilir kod içeremez.  
  
 Uygulama için bir uydu derleme aşağıdaki Al.exe komut oluşturur `Example` Almanca kaynakları dosya strings.de.resources gelen.  
  
```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll  
```  
  
 Aşağıdaki Al.exe komut ayrıca uygulama için bir uydu derleme oluşturur `Example` dosya strings.de.resources gelen. **/Template** seçenek kültür bilgilerini hariç tüm derleme meta verilerini üst derleme (Example.dll) devralmak uydu derlemesi neden olur.  
  
```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll  
```  
  
 Aşağıdaki tabloda daha ayrıntılı bu komutları kullanılan Al.exe seçenekleri açıklanmaktadır.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**-Hedef:**lib|Uydu derlemenizi kitaplığı (.dll) dosyasına derlenir belirtir. Uydu derlemesi yürütülebilir kod içermiyor ve bir uygulamanın ana derleme olmadığından uydu derlemelerini DLL'ler olarak kaydetmeniz gerekir.|  
|**-katıştırmak:**strings.de.resources|Al.exe derleme derlediğinde katıştırmak için kaynak dosya adını belirtir. Uydu bütünleştirilmiş kodunda birden fazla .resources dosyaları eklenebilir, ancak hub ve bağlı bileşen modeli izliyorsanız, her kültür için bir uydu derlemesi derlemeniz gerekir. Ancak, dizeleri ve nesneler için ayrı .resources dosyaları oluşturabilirsiniz.|  
|**-kültür:**Gizle|Derlemek için kaynak kültürü belirtir. Belirtilen kültür için kaynakları için aradığında ortak dil çalışma zamanı bu bilgileri kullanır. Bu seçeneği atlayın, Al.exe kaynak derleme, ancak çalışma zamanı bir kullanıcı bulmak mümkün olmaz ister.|  
|**-out:**Example.resources.dll|Çıktı dosyası adını belirtir. Ad adlandırma standardı izlemelidir *baseName*.resources. *Uzantı*, burada *baseName* ana derleme adıdır ve *uzantısı* geçerli dosya adı uzantısıdır (örneğin, .dll). Çalışma zamanı, çıkış dosyasının adına dayanarak bir uydu derleme kültürünü belirlemek mümkün olmadığını unutmayın; kullanmalısınız **/kültür** belirlemek için seçeneği.|  
|**-Şablon:**Example.dll|Uydu derlemesi kültür alanı dışında tüm derleme meta verilerini devralır derleme belirtir. Bu seçenek, uydu derlemelerini etkiler, yalnızca sahip bir derleme belirtirseniz bir [güçlü ad](../../../docs/framework/app-domains/strong-named-assemblies.md).|  
  
 Al.exe ile kullanılabilir seçenekler tam bir listesi için bkz: [derleme bağlayıcı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
## <a name="satellite-assemblies-an-example"></a>Uydu derlemeleri: Örnek  
 Yerelleştirilmiş Tebrik içeren bir ileti kutusu görüntüler basit bir "Hello world" örnek verilmiştir. İngilizce (ABD), Fransızca (Fransa) ve Rusça (Rusya) kültürler için örnek kaynaklar içerir ve geri dönüş kültürü İngilizce'dir. Örnek oluşturmak için aşağıdakileri yapın:  
  
1.  Greeting.resx veya Greeting.txt varsayılan kültür için kaynak içerecek şekilde adlı bir kaynak dosyası oluşturun. Adlı tek bir dize depolamak `HelloString` "Hello world!" değeri olan Bu dosyada.  
  
2.  İngilizce (TR) uygulamanın varsayılan kültürü olduğunu belirtmek için aşağıdaki ekleyin <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> uygulamanın AssemblyInfo dosyası veya uygulamanın ana derlemeye derlenmiş ana kaynak kodu dosyasına özniteliği.  
  
     [!code-csharp[Conceptual.Resources.Locating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
     [!code-vb[Conceptual.Resources.Locating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3.  Ek kültürler (en-US, fr-FR ve ru-RU) için destek uygulamayı aşağıdaki şekilde ekleyin:  
  
    -   En-US veya İngilizce (ABD) kültür desteklemek için Greeting.en US.resx veya Greeting.en US.txt adlı bir kaynak dosyası oluşturun ve bunu adlı tek bir dize depolamak `HelloString` "Hi world!" değeri olan  
  
    -   Fr-FR veya Fransızca (Fransa) kültür desteklemek için Greeting.fr FR.resx veya Greeting.fr FR.txt adlı bir kaynak dosyası oluşturun ve bunu adlı tek bir dize depolamak `HelloString` "Salut tout le monde!" değeri olan  
  
    -   Ru-RU veya Rusça (Rusya) kültür desteklemek için Greeting.ru RU.resx veya Greeting.ru RU.txt adlı bir kaynak dosyası oluşturun ve bunu adlı tek bir dize depolamak `HelloString` "Всем привет!" değeri olan  
  
4.  Kullanım [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) her bir metin veya ikili .resources dosyası XML kaynak dosyasına derlemek için. Çıkış, kök dosya adıyla aynı .resx veya .txt dosyaları, ancak bir .resources uzantısına sahip dosyalar kümesidir. Visual Studio ile örnek oluşturursanız, derleme işlemi otomatik olarak gerçekleştirilir. Visual Studio kullanmıyorsanız, .resx dosyaları .resources dosyalarıyla derlemek için aşağıdaki komutları çalıştırın:  
  
    ```console
    resgen Greeting.resx  
    resgen Greeting.en-us.resx  
    resgen Greeting.fr-FR.resx  
    resgen Greeting.ru-RU.resx  
    ```  
  
     XML dosyaları yerine metin dosyalarında kaynaklarınız varsa, .resx uzantısı .txt ile değiştirin.  
  
5.  Aşağıdaki kaynak kodu varsayılan kültür için kaynaklar yanı sıra uygulamanın ana derlemeye derleyin:  
  
    > [!IMPORTANT]
    >  Örnek oluşturmak için Visual Studio yerine komut satırı kullanıyorsanız çağrısı değiştirmelisiniz <xref:System.Resources.ResourceManager> şu sınıfı oluşturucusu: `ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`  
  
     [!code-csharp[Conceptual.Resources.Locating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
     [!code-vb[Conceptual.Resources.Locating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]  
  
     Örnek uygulama adı ve komut satırından derleme, C# derleyici komut şöyledir:  
  
    ```console  
    csc Example.cs -res:Greeting.resources  
    ```  
  
     Karşılık gelen Visual Basic derleyici komut şöyledir:  
  
    ```console  
    vbc Example.vb -res:Greeting.resources  
    ```  
  
6.  Uygulama tarafından desteklenen her yerelleştirilmiş kültür için ana uygulama dizinindeki bir dizin oluşturun. Bir en-US, fr-FR ve ru-RU alt oluşturmanız gerekir. Bu alt dizinleri, Visual Studio derleme işleminin bir parçası otomatik olarak oluşturur.  
  
7.  Uydu derlemeleri tek tek kültüre özgü .resources dosyaları ekleme ve uygun dizinine kaydedin. Bunu yapmak için her .resources dosyası için bir komut şöyledir:  
  
    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll  
    ```  
  
     Burada *kültür* kaynakları uydu derleme içeren kültür adı. Visual Studio bu işlemi otomatik olarak işler.  
  
 Bu örnek daha sonra çalıştırabilirsiniz. Bu rastgele desteklenen birini yapacak geçerli kültürü cultures ve yerelleştirilmiş Tebrik görüntüler.  
  
<a name="SN"></a>   
## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a>Uydu derlemeleri genel derleme önbelleğine yükleme  
 Yerel uygulama alt dizinindeki derlemelerini yüklemek yerine, genel derleme önbelleğinde yükleyebilirsiniz. Sınıf kitaplıkları ve birden çok uygulama tarafından kullanılan sınıf kitaplığı kaynak derlemeleri varsa, bu özellikle yararlıdır.  
  
 Genel derleme önbelleğinde derlemeleri yükleme tanımlayıcı adlar sahip olmasını gerektirir. Tanımlayıcı adlı derlemeler ile geçerli bir ortak/özel anahtar çifti imzalanmıştır. Çalışma zamanı hangi derleme bağlama isteği karşılamak için kullanılacağını belirlemek için kullanır sürüm bilgilerini içerir. Tanımlayıcı adlar ve sürüm oluşturma hakkında daha fazla bilgi için bkz: [derleme sürümü oluşturma](../../../docs/framework/app-domains/assembly-versioning.md). Tanımlayıcı adlar hakkında daha fazla bilgi için bkz: [Strong-Named derlemeler](../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
 Bir uygulama geliştirirken, son ortak/özel anahtar çifti erişimi sahip düşüktür. Bir derlemeyi genel derleme önbelleğinde yüklemek ve beklendiği gibi çalıştığından emin olmak için Gecikmeli imzalama adı verilen bir tekniği kullanabilirsiniz. Derleme zamanında oturum bütünleştirilmiş gecikme, dosyanın sağlam ad imzası için alan ayırın. Daha sonra gerçek imzalama gecikti son ortak/özel anahtar çifti olduğunda kullanılabilir. Gecikmeli imzalama hakkında daha fazla bilgi için bkz: [Gecikmeli bir derleme imzalama](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
### <a name="obtaining-the-public-key"></a>Ortak anahtarı edinme  
 Oturum bütünleştirilmiş geciktirmek için ortak anahtar erişiminiz olmalıdır. Ya da gerçek ortak anahtarı kuruluş tarafından nihai imzalama yapın veya ortak anahtar kullanarak oluşturmak, şirketinizdeki alabilirsiniz [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).  
  
 Aşağıdaki Sn.exe komut bir test ortak/özel anahtar çifti oluşturur. **– K** seçeneği belirtir Sn.exe'nin yeni bir anahtar çifti oluşturma ve TestKeyPair.snk adlı bir dosyaya kaydedin.  
  
```console
sn –k TestKeyPair.snk   
```  
  
 Ortak anahtar test anahtar çiftini içeren dosyasından ayıklayabilirsiniz. Aşağıdaki komut ortak anahtar TestKeyPair.snk ayıklar ve içinde PublicKey.snk kaydeder:  
  
```console
sn –p TestKeyPair.snk PublicKey.snk  
```  
  
### <a name="delay-signing-an-assembly"></a>Derleme İmzalamayı Geciktirme  
 Ortak anahtar oluşturma veya alma sonra kullandığınız [derleme bağlayıcı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) derlemeyi derlemek ve belirtmek için imzalama ertelendi.  
  
 Aşağıdaki Al.exe komutu StringLibrary uygulama için bir uydu tanımlayıcı adlı derleme strings.ja.resources dosyasından oluşturur:  
  
```console 
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk  
```  
  
 **-Gecikme +** seçeneği, derleme bağlayıcı derlemenin imzalanmasını gecikme belirtir. **- Keyfile** seçeneği, gecikme için kullanılacak ortak anahtarı içeren anahtar dosyasının adını derleme oturum belirtir.  
  
### <a name="re-signing-an-assembly"></a>Bir derlemeyi yeniden imzalama  
 Uygulamanızı dağıtmadan önce gecikme yeniden imzalamalısınız uydu derleme gerçek anahtar çifti ile imzalanmamış. Sn.exe kullanarak bunu yapabilirsiniz.  
  
 Aşağıdaki Sn.exe komutu StringLibrary.resources.dll RealKeyPair.snk dosyasında depolanan anahtar çifti ile imzalar. **– R** seçeneği belirtir daha önce imzalanmış veya gecikme imzalı derlemedir yeniden imzalanması gerekir.  
  
```console
sn –R StringLibrary.resources.dll RealKeyPair.snk   
```  
  
### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a>Bir derlemeyi genel derleme önbelleğinde yükleme  
 Çalışma zamanı için kaynak geri dönüş işlemi kaynaklarında aradığında, görünüyor [genel derleme önbelleği](../../../docs/framework/app-domains/gac.md) ilk. (Daha fazla bilgi için "Kaynak geri dönüş işlemi" bölümüne bakın [paketleme ve dağıtma kaynakları](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) konu.) Bir uydu derleme güçlü bir ad ile imzalandığında hemen genel derleme önbelleğinde kullanılarak yüklenebilir [Genel Derleme Önbelleği Aracı (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
 Aşağıdaki Gacutil.exe komutu StringLibrary.resources.dll genel derleme önbelleğinde yükler:  
  
```console
gacutil -i:StringLibrary.resources.dll  
```  
  
 **/İ** seçeneği, Gacutil.exe belirtilen derleme genel derleme önbelleğine yüklemeniz gerekip gerekmediğini belirtir. Uydu sonra uydu derlemesi kullanmak üzere tasarlanmış tüm uygulamalar için kullanılabilir hale içerdiği kaynakların önbelleğinde derleme yüklenir.  
  
### <a name="resources-in-the-global-assembly-cache-an-example"></a>Genel Derleme Önbelleği kaynaklarında: örneği  
 Aşağıdaki örnek ayıklamak ve bir kaynak dosyasından yerelleştirilmiş Tebrik dönmek için bir .NET Framework Sınıf Kitaplığı'nda bir yöntem kullanır. Kitaplık ve kaynaklarına genel derleme önbelleğinde kaydedilir. Örneğin İngilizce (ABD), Fransızca (Fransa), Rusça (Rusya) ve İngilizce kültürler için kaynakları içerir. İngilizce varsayılan kültürdür; kaynaklarıyla ana derlemede depolanır. Kitaplık ve kendisine ait bir ortak anahtar ile uydu derlemelerini daha sonra yeniden oturum açtığında bunları ortak/özel anahtar çifti ile işaretlerini başlangıçta gecikme örnek. Örnek oluşturmak için aşağıdakileri yapın:  
  
1.  Visual Studio kullanmıyorsanız, aşağıdaki kullanın [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) komutu ResKey.snk adlı bir genel/özel anahtar çifti oluşturmak için:  
  
    ```console
    sn –k ResKey.snk  
    ```  
  
     Visual Studio kullanıyorsanız **imzalama** Proje sekmesinde **özellikleri** anahtar dosyası oluşturmak için iletişim kutusu.  
  
2.  Aşağıdaki [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) komutu PublicKey.snk adlı ortak bir anahtar dosyası oluşturmak için:  
  
    ```console
    sn –p ResKey.snk PublicKey.snk  
    ```  
  
3.  Varsayılan kültür için kaynak içerecek şekilde Strings.resx adlı bir kaynak dosyası oluşturun. Adlı tek bir dize depolamak `Greeting` değeri olan "Nasıl you musunuz?" Bu dosyada.  
  
4.  "En" uygulamanın varsayılan kültürü olduğunu belirtmek için aşağıdaki ekleyin <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> özniteliği uygulamanın AssemblyInfo dosyası veya uygulamanın ana derlemeye derlenmiş ana kaynak kodu dosyasına:  
  
     [!code-csharp[Conceptual.Resources.Satellites#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
     [!code-vb[Conceptual.Resources.Satellites#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]  
  
5.  Ek kültürler (en-US, fr-FR ve ru-RU kültürler) için destek uygulamayı aşağıdaki şekilde ekleyin:  
  
    -   "En-US" veya İngilizce (ABD) kültür desteklemek için Strings.en US.resx veya Strings.en US.txt adlı bir kaynak dosyası oluşturun ve bunu adlı tek bir dize depolamak `Greeting` değeri olan "Hello!".  
  
    -   "Fr-FR" veya Fransızca (Fransa) kültür desteklemek için Strings.fr FR.resx veya Strings.fr FR.txt adlı bir kaynak dosyası oluşturun ve bunu adlı tek bir dize depolamak `Greeting` "İyi günlüğü!" değeri olan  
  
    -   "Ru-RU" veya Rusça (Rusya) kültür desteklemek için Strings.ru RU.resx veya Strings.ru RU.txt adlı bir kaynak dosyası oluşturun ve bunu adlı tek bir dize depolamak `Greeting` "Привет!" değeri olan  
  
6.  Kullanım [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) her bir metin veya ikili .resources dosyası XML kaynak dosyasına derlemek için. Çıkış, kök dosya adıyla aynı .resx veya .txt dosyaları, ancak bir .resources uzantısına sahip dosyalar kümesidir. Visual Studio ile örnek oluşturursanız, derleme işlemi otomatik olarak gerçekleştirilir. Visual Studio kullanmıyorsanız, .resx dosyaları .resources dosyalarıyla derlemek için aşağıdaki komutu çalıştırın:  
  
    ```console
    resgen filename  
    ```  
  
     Burada *filename* isteğe bağlı yol, dosya adı ve uzantısı .resx veya metin dosyası.  
  
7.  Aşağıdaki kaynak kodu derleyin StringLibrary.vb veya StringLibrary.cs için bir gecikme içine varsayılan kültür için kaynaklar birlikte StringLibrary.dll adlı kitaplığı derleme imzalanmamış:  
  
    > [!IMPORTANT]
    >  Örnek oluşturmak için Visual Studio yerine komut satırı kullanıyorsanız çağrısı değiştirmelisiniz <xref:System.Resources.ResourceManager> sınıfı oluşturucuya `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.  
  
     [!code-csharp[Conceptual.Resources.Satellites#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
     [!code-vb[Conceptual.Resources.Satellites#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]  
  
     C# derleyici komut şöyledir:  
  
    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs  
    ```  
  
     Karşılık gelen Visual Basic derleyici komut şöyledir:  
  
    ```console  
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb  
    ```  
  
8.  Uygulama tarafından desteklenen her yerelleştirilmiş kültür için ana uygulama dizinindeki bir dizin oluşturun. Bir en-US, fr-FR ve ru-RU alt oluşturmanız gerekir. Bu alt dizinleri, Visual Studio derleme işleminin bir parçası otomatik olarak oluşturur. Tüm uydu derlemelerini aynı dosya adına sahip olduğundan, alt dizinleri ortak/özel anahtar çifti ile imzalanmış kadar tek tek kültüre özgü uydu derlemeleri depolamak için kullanılır.  
  
9. Tek tek ekleme kültüre özgü .resources dosyaları imzalı gecikme içine uydu derlemeleri ve bunları uygun dizinine kaydedin. Bunu yapmak için her .resources dosyası için bir komut şöyledir:  
  
    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk  
    ```  
  
     Burada *kültür* bir kültür adı. Bu örnekte kültür en-US, fr-FR ve ru-RU adlarıdır.  
  
10. StringLibrary.dll kullanarak yeniden oturum [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) gibi:  
  
    ```console
    sn –R StringLibrary.dll RealKeyPair.snk  
    ```  
  
11. Tek tek uydu derlemelerini yeniden oturum açın. Bunu yapmak için kullanın [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) gibi her uydu derlemesi için:  
  
    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk  
    ```  
  
12. StringLibrary.dll ve her biri kendi uydu derlemeleri genel derleme önbelleğinde aşağıdaki komutu kullanarak kaydedin:  
  
    ```console
    gacutil -i filename  
    ```  
  
     Burada *filename* kaydetmek için dosyayı adıdır.  
  
13. Visual Studio kullanıyorsanız, yeni bir oluşturma **konsol uygulaması** adlı projesi `Example`StringLibrary.dll başvuru ve aşağıdaki kaynak kodu ekleyin ve derleyin.  
  
     [!code-csharp[Conceptual.Resources.Satellites#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
     [!code-vb[Conceptual.Resources.Satellites#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]  
  
     Komut satırından derlemek için C# derleyici için aşağıdaki komutu kullanın:  
  
    ```console
    csc Example.cs -r:StringLibrary.dll   
    ```  
  
     Visual Basic derleyici komut satırı şöyledir:  
  
    ```console
    vbc Example.vb -r:StringLibrary.dll   
    ```  
  
14. Example.exe çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynakları Paketleme ve Dağıtma](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [Bütünleştirilmiş Kod İmzalamayı Geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [Sn.exe (Tanımlayıcı Ad Aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)
