---
title: Masaüstü Uygulamaları için Uydu Derlemeleri Oluşturma
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1aecd8e6dcec73ba4dc45d4bf8f365503888687e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295997"
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a>Masaüstü Uygulamaları için Uydu Derlemeleri Oluşturma
Kaynak dosyaları, yerelleştirilmiş uygulamalar olarak merkezi bir rol oynar. Bunlar, bir uygulama kullanıcının kendi dil ve kültür dizeler, görüntüler ve diğer verileri görüntüler ve kullanıcının kendi dil veya kültür için kaynaklar kullanılamıyorsa, alternatif veri sağlamak için etkinleştirin. .NET Framework, bulun ve yerelleştirilmiş kaynakları almak için bir hub-and-spoke modelini kullanır. Yerelleştirilemeyen yürütülebilir kod ve nötr olarak adlandırılan tek bir kültür için kaynakları içeren ana derleme hub'ı olan veya varsayılan kültür. Geri dönüş kültürü uygulamanın varsayılan kültürüdür; hiçbir yerelleştirilmiş kaynaklar kullanılabilir olduğunda kullanılır. Kullandığınız <xref:System.Resources.NeutralResourcesLanguageAttribute> kültürü uygulamanın varsayılan kültürünü belirtmek için özniteliği. Her bir uçtaki tek bir yerelleştirilmiş kültür için kaynaklar içeriyor ancak hiçbir kod içermiyor bir uydu derlemeye bağlanır. Uydu derlemeleri ana derlemenin parçası olmadığından, kolayca güncelleştirmek veya uygulamanın ana derlemesini değiştirmeden belirli bir kültüre karşılık gelen kaynakları değiştirin.  
  
> [!NOTE]
>  Bir uygulamanın varsayılan kültürünü kaynaklarını bir uydu derlemesine da depolanabilir. Bunu yapmak için Ata <xref:System.Resources.NeutralResourcesLanguageAttribute> değeri öznitelik <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>.  
  
## <a name="satellite-assembly-name-and-location"></a>Uydu derleme adı ve konumu  
 Bunlar kolayca bulunan kaldırılabilir ve böylece kaynakları belirli konumlara yerleştirin hub-and-spoke modelini gerektirir. Beklendiği gibi değil derleme ve adı kaynakları yapmak veya bunları doğru konumda yerleştirmeyin, ortak dil çalışma zamanı bunları bulmanız mümkün olmayacaktır ve varsayılan kültürün kaynakları yerine kullanır. .NET Framework kaynak tarafından temsil edilen Yöneticisi bir <xref:System.Resources.ResourceManager> nesne, otomatik olarak yerelleştirilmiş kaynaklara erişmek için kullanılır. Kaynak Yöneticisi için aşağıdakiler gereklidir:  
  
-   Tek bir uydu derlemesi, belirli bir kültüre ait tüm kaynakları içermelidir. Diğer bir deyişle, bir tek bir ikili .resources dosyasına birden çok .txt veya .resx dosyalarına derlemeniz gerekir.  
  
-   Uygulama dizininde, kültürün kaynakları depolayan her yerelleştirilmiş kültür için ayrı bir alt dizin olmalıdır. Alt ad kültür adı ile aynı olmalıdır. Alternatif olarak, genel derleme önbelleğinde uydu bütünleştirilmiş kodlarınızı depolayabilirsiniz. Bu durumda, derlemenin tanımlayıcı ad kültür bilgilerini bileşeninin kültürü belirtmeniz gerekir. (Bkz [yükleme uydu derlemeleri genel derleme önbelleğinde](#SN) bu konunun ilerleyen bölümlerinde.)  
  
    > [!NOTE]
    >  Uygulamanızı subcultures için kaynaklar içeriyorsa, her alt ayrı bir alt dizinde uygulama dizinine yerleştirin. Kendi ana kültürün dizin alt dizinler subcultures yerleştirmeyin.  
  
-   Uydu derleme uygulama ile aynı ada sahip olmalıdır ve dosya adı uzantısını kullanmanız gerekir ". resources.dll". Örneğin, bir uygulama Example.exe adlandırılmışsa, her bir uydu derlemesini adını Example.resources.dll olmalıdır. Uydu derleme adı kaynak dosya kültürünü göstermez unutmayın. Ancak, uydu derleme kültürü belirten bir dizinde görünür.  
  
-   Uydu derlemesinin kültürle ilgili bilgileri derlemenin meta verilerde eklenmesi gerekir. Kültür adı uydu derleme meta verilerini depolamak için belirttiğiniz `/culture` seçeneğini kullandığınızda [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md) kaynakları uydu derlemede katıştırmak için.  
  
 İçinde yüklemiyorsanız uygulamalar için bir örnek dizin yapısını ve konum gereksinimleri aşağıdaki çizimde [genel derleme önbelleği](../../../docs/framework/app-domains/gac.md). .Txt ve .resources uzantılı öğeleri son uygulama ile gelmeyecektir. Bu, son uydu kaynak derlemeleri oluşturmak için kullanılan ara kaynak dosyalarıdır. Bu örnekte, .resx dosyalarını .txt dosyaları için alternatif. Daha fazla bilgi için [kaynakları paketleme ve dağıtma](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). 
 
 Aşağıdaki görüntüde, uydu derleme dizini gösterilmektedir:
  
 ![Bir uydu derleme dizinle yerelleştirilmiş alt dizinleri.](./media/creating-satellite-assemblies-for-desktop-apps/satellite-assembly-directory.gif)
  
## <a name="compiling-satellite-assemblies"></a>Uydu derlemelerini derleme  
 Kullandığınız [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) metin dosyalarını veya ikili .resources dosyalarına kaynakları içeren XML (.resx) dosyalarını derlemek için. Daha sonra [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) .resources dosyalarını uydu derlemeler içinde derlemek için. Al.exe .resources dosyaları, belirttiğiniz bir derleme oluşturur. Uydu derlemeleri yalnızca kaynakları içerebilir. herhangi bir yürütülebilir kod içeremezler.  
  
 Uygulama için bir uydu derleme aşağıdaki Al.exe komut oluşturur `Example` Almanca kaynakları dosya strings.de.resources öğesinden.  
  
```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll  
```  
  
 Aşağıdaki Al.exe komutu ayrıca uygulama için bir uydu derlemesi oluşturur `Example` dosya strings.de.resources öğesinden. **/Template** seçeneği üst derlemeden (Example.dll) kültür bilgilerini dışında tüm derleme meta verileri devralmak uydu derleme neden olur.  
  
```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll  
```  
  
 Aşağıdaki tabloda, bu komutların ayrıntılı kullanılan Al.exe seçeneklerini açıklar.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**-Hedef:** lib|Uydu bütünleştirilmiş kodunuzda bir kitaplık (.dll) dosyasına derlenir belirtir. Bir uydu derleme yürütülebilir kodu içermiyor ve bir uygulamanın ana derleme olmadığından, uydu derlemeleri dll kaydetmeniz gerekir.|  
|**-ekleme:** strings.de.resources|Al.exe derleme derlediğinde eklemek için kaynak dosyasının adını belirtir. Birden çok .resources dosyasına bir uydu derlemesine gömebilirsiniz ancak hub-and-spoke modelini izliyorsanız, her bir kültür için bir uydu derleme derlemeniz gerekir. Ancak, dizeleri ve nesneler için ayrı .resources dosyaları oluşturabilirsiniz.|  
|**-culture:** Gizle|Kaynak derleme kültürü belirtir. Belirtilen bir kültürün kaynaklarını aradığında, ortak dil çalışma zamanı bu bilgileri kullanır. Bu seçeneği atlarsanız, Al.exe hala kaynak derlenir, ancak çalışma zamanı bir kullanıcı bulmak mümkün olmayacaktır, ister.|  
|**-out:** Example.resources.dll|Çıkış dosyasının adını belirtir. Ad adlandırma standardı izlemelidir *baseName*.resources. *Uzantı*burada *baseName* ana derlemenin adıdır ve *uzantısı* geçerli dosya adı uzantısıdır (örneğin, .dll). Çalışma zamanı, çıkış dosyasının adına dayanarak bir uydu derleme kültürü belirlemek mümkün olmadığını unutmayın; kullanmalısınız **/kültür** seçeneği belirlemek için.|  
|**-Şablon:** Example.dll|Uydu derlemesini kültür alanı dışında tüm derleme meta verilerinin devralacak bir derleme belirtir. Bu seçenek, uydu derlemeleri etkiler, yalnızca sahip bir derleme belirtirseniz bir [tanımlayıcı ad](../../../docs/framework/app-domains/strong-named-assemblies.md).|  
  
 Al.exe ile kullanılabilen seçenekleri tam bir listesi için bkz. [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
## <a name="satellite-assemblies-an-example"></a>Uydu derlemeleri: Bir Örnek  
 Yerelleştirilmiş bir karşılama içeren bir ileti kutusu görüntüleyen basit bir "Hello world" örnek verilmiştir. İngilizce (Amerika Birleşik Devletleri), Fransızca (Fransa) ve Rusça (Rusya) kültürleri için örnek kaynakları içerir ve geri dönüş kültürü İngilizce olarak. Örneği oluşturmak için aşağıdakileri yapın:  
  
1. Greeting.resx veya Greeting.txt varsayılan kültürünün kaynak içerecek şekilde adlı bir kaynak dosyası oluşturun. Adlı tek bir dize Store `HelloString` "Hello world!" değeri olan Bu dosyada.  
  
2. İngilizce (TR) uygulamanın varsayılan kültürünü olduğunu belirtmek için aşağıdakileri ekleyin <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> özniteliği uygulamanın AssemblyInfo dosyası veya uygulamanın ana bütünleştirilmiş kod içine derlenmiş ana kaynak kodu dosyası.  
  
     [!code-csharp[Conceptual.Resources.Locating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
     [!code-vb[Conceptual.Resources.Locating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3. Ek kültürleri (en-US, fr-FR ve ru-RU) için destek uygulamaya aşağıdaki şekilde ekleyin:  
  
    -   En-US veya İngilizce (ABD) kültürü desteklemek için Greeting.en-US.resx veya Greeting.en US.txt adlı bir kaynak dosyası oluşturun ve adlı tek bir dize depolamak `HelloString` "Merhaba Dünya!" değeri olan  
  
    -   Fr-FR ya da Fransızca (Fransa) kültürü desteklemek için Greeting.fr-FR.resx veya Greeting.fr FR.txt adlı bir kaynak dosyası oluşturun ve adlı tek bir dize depolamak `HelloString` "Salut tout le monde!" değeri olan  
  
    -   Ru-RU veya Rusça (Rusya) kültürü desteklemek için Greeting.ru RU.resx veya Greeting.ru RU.txt adlı bir kaynak dosyası oluşturun ve adlı tek bir dize depolamak `HelloString` "Всем привет!" değeri olan  
  
4. Kullanım [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) her bir metin veya XML kaynak dosyası bir ikili .resources dosyasına derlemek için. Çıktı, .resx veya .txt dosyaları, ancak bir .resources uzantısını olarak aynı kök dosya adı olan dosyalar kümesidir. Örneğin Visual Studio ile oluşturma, derleme işlemi otomatik olarak gerçekleştirilir. Visual Studio kullanmıyorsanız, .resx dosyalarını .resources dosyalarına derlemek için aşağıdaki komutları çalıştırın:  
  
    ```console
    resgen Greeting.resx  
    resgen Greeting.en-us.resx  
    resgen Greeting.fr-FR.resx  
    resgen Greeting.ru-RU.resx  
    ```  
  
     XML dosyaları yerine metin dosyalarında kaynaklarınız varsa, .resx uzantısına .txt ile değiştirin.  
  
5. Aşağıdaki kaynak kodu kaynaklar için varsayılan kültürü yanı sıra, uygulamanın ana derlemeye derleyin:  
  
    > [!IMPORTANT]
    >  Örneği oluşturmak için komut satırı yerine Visual Studio kullanıyorsanız, çağrı değiştirmelisiniz <xref:System.Resources.ResourceManager> aşağıdaki sınıf oluşturucusuna: `ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`  
  
     [!code-csharp[Conceptual.Resources.Locating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
     [!code-vb[Conceptual.Resources.Locating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]  
  
     Uygulama örneği olarak adlandırılır ve komutu için komut satırından derlediğiniz C# derleyici:  
  
    ```console  
    csc Example.cs -res:Greeting.resources  
    ```  
  
     Karşılık gelen Visual Basic derleyici komut şöyledir:  
  
    ```console  
    vbc Example.vb -res:Greeting.resources  
    ```  
  
6. Uygulamanın desteklediği her bir yerelleştirilmiş kültür için ana uygulama dizininde bir dizin oluşturun. En-US, fr-FR ve ru-RU alt oluşturmanız gerekir. Bu alt dizinleri, Visual Studio derleme işleminin bir parçası otomatik olarak oluşturur.  
  
7. Uydu derlemeler içinde tek bir kültüre özgü .resources dosyaları ekleme ve bunları uygun dizine kaydedin. Bunu yapmak için her bir .resources dosyası için komut şöyledir:  
  
    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll  
    ```  
  
     Burada *kültür* kaynakları uydu bütünleştirilmiş kod içeren kültür adı. Visual Studio bu işlemi otomatik olarak işler.  
  
 Örnek daha sonra çalıştırabilirsiniz. Bu rastgele desteklenen birini yapacak cultures geçerli kültürü ve yerelleştirilmiş bir karşılama görüntüleyen.  
  
<a name="SN"></a>   
## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a>Uydu derlemeleri genel derleme önbelleğine yükleme  
 Bir yerel uygulama alt dizinine derlemeleri yüklemek yerine, genel derleme önbelleğine yükleyebilirsiniz. Sınıf kitaplıkları ve birden çok uygulama tarafından kullanılan sınıf kitaplığı kaynak derlemeler varsa, bu özellikle yararlıdır.  
  
 Genel derleme önbelleğinde derlemeleri yükleme tanımlayıcı adlara sahip olmasını gerektirir. Tanımlayıcı adlandırılmış derlemeler, geçerli bir ortak/özel anahtar çifti ile imzalanmış. Çalışma zamanının hangi derleme bağlama isteğini yerine getirmek için kullanılacağını belirlemek için kullandığı sürüm bilgileri içerirler. Güçlü adlar ve sürüm oluşturma hakkında daha fazla bilgi için bkz: [derleme sürümlendirme](../../../docs/framework/app-domains/assembly-versioning.md). Güçlü adlar hakkında daha fazla bilgi için bkz: [Strong-Named derlemeleri](../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
 Bir uygulama geliştirirken, son ortak/özel anahtar çifti erişimi olacağını düşüktür. Uydu derlemesi genel derleme önbelleğine yüklemek ve beklendiği gibi çalıştığından emin olmak için Gecikmeli imzalamayı olarak adlandırılan tekniği kullanabilirsiniz. Derlemeyi imzala gecikme, oluşturma zamanında dosyanın tanımlayıcı ad imzası için alan ayırın. Daha sonra gerçek imzalama ertelendi son ortak/özel anahtar çifti ne zaman kullanılabilir. Gecikmeli imzalama hakkında daha fazla bilgi için bkz. [derlemeyi imzalamayı geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
### <a name="obtaining-the-public-key"></a>Ortak anahtarı edinme  
 Derlemeyi imzala geciktirmek için ortak anahtarına erişimi olmalıdır. Ya da gerçek ortak anahtarı kuruluştan şirketinizdeki nihai imzalama yapın veya bir ortak anahtar kullanarak oluşturma alabilirsiniz [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).  
  
 Aşağıdaki Sn.exe komut bir test ortak/özel anahtar çifti oluşturur. **– K** Sn.exe yeni bir anahtar çifti oluşturma ve TestKeyPair.snk adlı bir dosyaya kaydet seçeneğini belirtir.  
  
```console
sn –k TestKeyPair.snk   
```  
  
 Test anahtar çiftini içeren dosyasından ortak anahtar ayıklayabilirsiniz. Aşağıdaki komut, TestKeyPair.snk ortak anahtarı ayıklar ve içinde PublicKey.snk kaydeder:  
  
```console
sn –p TestKeyPair.snk PublicKey.snk  
```  
  
### <a name="delay-signing-an-assembly"></a>Derleme İmzalamayı Geciktirme  
 Ortak anahtarı oluşturma veya alma sonra kullandığınız [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) Gecikmeli imzalama bütünleştirilmiş kodu derler ve belirtin.  
  
 Aşağıdaki Al.exe komutu StringLibrary uygulama için bir uydu tanımlayıcı adlı derleme strings.ja.resources dosyasından oluşturur:  
  
```console 
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk  
```  
  
 **-Gecikme +** seçeneği Assembly Linker derlemenin imzalanmasını gecikme belirtir. **- Keyfile** seçeneği oturum derleme geciktirmek için kullanılacak ortak anahtarı içeren anahtar dosyasının adını belirtir.  
  
### <a name="re-signing-an-assembly"></a>Bir derlemeyi yeniden imzalama  
 Uygulamanızı dağıtmadan önce gecikme süresini yeniden imzalamanız gerekir uydu derlemesi gerçek anahtar çifti ile imzalanmış. Sn.exe kullanarak bunu yapabilirsiniz.  
  
 Aşağıdaki Sn.exe komutunu StringLibrary.resources.dll RealKeyPair.snk dosyasında depolanan anahtar çifti ile imzalar. **– R** seçeneği belirtir, daha önce imzalanmış veya gecikmeli imzalanmış derlemesidir yeniden imzalanması gerekir.  
  
```console
sn –R StringLibrary.resources.dll RealKeyPair.snk   
```  
  
### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a>Uydu derlemesi genel derleme önbelleğine yükleme  
 Çalışma zamanı için kaynak geri dönüş işlemi kaynaklarında ararken bakar [genel derleme önbelleği](../../../docs/framework/app-domains/gac.md) ilk. (Daha fazla bilgi için "Kaynak geri dönüş işlemi" bölümüne bakın. [kaynakları paketleme ve dağıtma](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) konu.) Bir uydu derleme güçlü bir adla imzalanır hemen sonra genel derleme önbelleğinde kullanarak yüklenebilir [Genel Derleme Önbelleği Aracı (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
 Aşağıdaki Gacutil.exe komutu StringLibrary.resources.dll genel bütünleştirilmiş kod önbelleğine yükler:  
  
```console
gacutil -i:StringLibrary.resources.dll  
```  
  
 **/İ** seçeneği Gacutil.exe belirtilen derlemeyi genel bütünleştirilmiş kod önbelleğine yüklemeniz gerekip gerekmediğini belirtir. Sonra uydu bütünleştirilmiş kod önbelleği, uydu derlemesini kullanmak üzere tasarlanmış tüm uygulamalar için kullanılabilir hale içerdiği tüm kaynakları yüklenir.  
  
### <a name="resources-in-the-global-assembly-cache-an-example"></a>Genel derleme önbelleğinde kaynaklar: Bir Örnek  
 Aşağıdaki örnek, ayıklamak ve bir kaynak dosyasından yerelleştirilmiş bir karşılama döndürmek için bir .NET Framework sınıf kitaplığında bir yöntem kullanır. Kitaplığını ve kaynaklarını genel derleme önbelleğinde kayıtlı. Örneğin, İngilizce (Amerika Birleşik Devletleri), Fransızca (Fransa), Rusça (Rusya) ve İngilizce kültürler için kaynakları içerir. İngilizce varsayılan kültürüdür; kaynaklarını ana derlemesinde depolanır. Örnek başlangıçta gecikme kitaplığı ve bir ortak anahtar ile uydu derlemelerini daha sonra yeniden imzalar bunları bir ortak/özel anahtar çifti ile imzalar. Örneği oluşturmak için aşağıdakileri yapın:  
  
1. Visual Studio kullanmıyorsanız, aşağıdaki kullanın [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) komutunu ResKey.snk adlı bir ortak/özel anahtar çifti oluşturun:  
  
    ```console
    sn –k ResKey.snk  
    ```  
  
     Visual Studio kullanıyorsanız, **imzalama** proje için sekmesinde **özellikleri** anahtar dosyası oluşturmak için iletişim kutusu.  
  
2. Aşağıdaki [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) komutunu PublicKey.snk adlı bir ortak anahtar dosyası oluşturun:  
  
    ```console
    sn –p ResKey.snk PublicKey.snk  
    ```  
  
3. Varsayılan kültürünün kaynak içerecek şekilde Strings.resx adlı bir kaynak dosyası oluşturun. Adlı tek bir dize Store `Greeting` değeri olan "Nasıl aldığınız musunuz?" Bu dosyada.  
  
4. "En" uygulamanın varsayılan kültürünü olduğunu belirtmek için aşağıdakileri ekleyin <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> özniteliği uygulamanın AssemblyInfo dosyası veya uygulamanın ana bütünleştirilmiş kod içine derlenmiş ana kaynak kod dosyasına:  
  
     [!code-csharp[Conceptual.Resources.Satellites#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
     [!code-vb[Conceptual.Resources.Satellites#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]  
  
5. Ek kültürleri (en-US, fr-FR ve ru-RU kültürler) için destek uygulamaya aşağıdaki şekilde ekleyin:  
  
    -   "En-US" ya da İngilizce (ABD) kültürü desteklemek için Strings.en-US.resx veya Strings.en US.txt adlı bir kaynak dosyası oluşturun ve adlı tek bir dize depolamak `Greeting` değeri olan "Hello!".  
  
    -   "Fr-FR" ya da Fransızca (Fransa) kültürü desteklemek için Strings.fr-FR.resx veya Strings.fr FR.txt adlı bir kaynak dosyası oluşturun ve adlı tek bir dize depolamak `Greeting` "İyi günlüğü!" değeri olan  
  
    -   Rusça (Rusya) kültürü ve "ru-RU" desteklemek için Strings.ru RU.resx veya Strings.ru RU.txt adlı bir kaynak dosyası oluşturun ve adlı tek bir dize depolamak `Greeting` "Привет!" değeri olan  
  
6. Kullanım [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) her bir metin veya XML kaynak dosyası bir ikili .resources dosyasına derlemek için. Çıktı, .resx veya .txt dosyaları, ancak bir .resources uzantısını olarak aynı kök dosya adı olan dosyalar kümesidir. Örneğin Visual Studio ile oluşturma, derleme işlemi otomatik olarak gerçekleştirilir. Visual Studio kullanmıyorsanız, .resx dosyalarını .resources dosyalarına derlemek için aşağıdaki komutu çalıştırın:  
  
    ```console
    resgen filename  
    ```  
  
     Burada *filename* isteğe bağlı bir yolu, dosya adı ve .resx veya metin dosyasının uzantısı.  
  
7. Aşağıdaki kaynak kodu derleyin StringLibrary.vb veya StringLibrary.cs kaynaklar için varsayılan kültürü bir gecikme ile birlikte StringLibrary.dll adlı kitaplık derlemesine imzalı:  
  
    > [!IMPORTANT]
    >  Örneği oluşturmak için komut satırı yerine Visual Studio kullanıyorsanız, çağrı değiştirmelisiniz <xref:System.Resources.ResourceManager> sınıf oluşturucusuna `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.  
  
     [!code-csharp[Conceptual.Resources.Satellites#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
     [!code-vb[Conceptual.Resources.Satellites#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]  
  
     Komut için C# derleyici:  
  
    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs  
    ```  
  
     Karşılık gelen Visual Basic derleyici komut şöyledir:  
  
    ```console  
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb  
    ```  
  
8. Uygulamanın desteklediği her bir yerelleştirilmiş kültür için ana uygulama dizininde bir dizin oluşturun. En-US, fr-FR ve ru-RU alt oluşturmanız gerekir. Bu alt dizinleri, Visual Studio derleme işleminin bir parçası otomatik olarak oluşturur. Tüm uydu derlemelerin aynı dosya adına sahip olduğundan, dizinler bireysel kültüre özel uydu derlemeler ortak/özel anahtar çifti ile imzalanmış kadar depolamak için kullanılır.  
  
9. Tek tek ekleme ertelenmiş olarak imzalandığında kültüre özgü .resources dosyalarına uydu bütünleştirilmiş kodlar ve bunları uygun dizine kaydedin. Bunu yapmak için her bir .resources dosyası için komut şöyledir:  
  
    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk  
    ```  
  
     Burada *kültür* bir kültür adı. Bu örnekte, kültür en-US, fr-FR ve ru-RU adlarıdır.  
  
10. StringLibrary.dll kullanarak yeniden oturum [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) gibi:  
  
    ```console
    sn –R StringLibrary.dll RealKeyPair.snk  
    ```  
  
11. Tek tek uydu derlemeleri yeniden oturum açın. Bunu yapmak için [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) gibi her bir uydu derlemesini için:  
  
    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk  
    ```  
  
12. StringLibrary.dll ve her biri kendi uydu derlemeleri genel derleme önbelleğinde aşağıdaki komutu kullanarak kaydedin:  
  
    ```console
    gacutil -i filename  
    ```  
  
     Burada *filename* kaydedilecek dosyanın adıdır.  
  
13. Visual Studio kullanıyorsanız, yeni bir oluşturma **konsol uygulaması** adlı proje `Example`StringLibrary.dll başvuru ve aşağıdaki kaynak kodunu ekleyin ve derleyin.  
  
     [!code-csharp[Conceptual.Resources.Satellites#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
     [!code-vb[Conceptual.Resources.Satellites#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]  
  
     Komut satırından derleme için aşağıdaki komutu kullanın. C# derleyici:  
  
    ```console
    csc Example.cs -r:StringLibrary.dll   
    ```  
  
     Visual Basic Derleyicisi için komut satırı verilmiştir:  
  
    ```console
    vbc Example.vb -r:StringLibrary.dll   
    ```  
  
14. Example.exe çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paketleme ve Dağıtma Kaynakları](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Derleme İmzalamayı Geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [Al.exe (Derleme Bağlayıcı)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [Sn.exe (Tanımlayıcı Ad Aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
- [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)
