---
title: Masaüstü Uygulamaları için Uydu Derlemeleri Oluşturma
description: Masaüstü uygulamaları için uydu derlemeleri oluşturmaya başlayın. Bir uydu derlemesi, yerelleştirilmiş kaynaklar sağlamak için kolayca güncelleştirilebilecek veya değiştirilebilir.
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
ms.openlocfilehash: be6603f3a593d9756d55204024214660b2220af3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166213"
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a>Masaüstü Uygulamaları için Uydu Derlemeleri Oluşturma

Kaynak dosyaları, yerelleştirilmiş uygulamalarda merkezi bir rol oynar. Bu uygulamalar, bir uygulamanın, kullanıcının kendi dilinde ve kültürüne yönelik dizeleri, resimleri ve diğer verileri görüntülemesini ve kullanıcının kendi dili ya da kültürüne yönelik kaynakların kullanılamaz durumda olup olmadığını alternatif veriler sağlamasını etkinleştirir. .NET Framework, yerelleştirilmiş kaynakları bulmak ve almak için bir hub ve bağlı bileşen modeli kullanır. Hub, yerelleştirilemeyen yürütülebilir kodu ve bağımsız veya varsayılan kültür olarak adlandırılan tek bir kültüre yönelik kaynakları içeren ana derlemedir. Varsayılan kültür, uygulamanın geri dönüş kültürüdür; kullanılabilir yerelleştirilmiş kaynaklar olmadığında kullanılır. <xref:System.Resources.NeutralResourcesLanguageAttribute>Uygulamanın varsayılan kültürünün kültürünü belirlemek için özniteliğini kullanırsınız. Her bir bağlı bileşen, tek bir yerelleştirilmiş kültürün kaynaklarını içeren bir uydu derlemesine bağlanır, ancak herhangi bir kod içermez. Uydu derlemeleri ana derlemenin parçası olmadığından, uygulamanın ana derlemesini değiştirmeden belirli bir kültüre karşılık gelen kaynakları kolayca güncelleştirebilir ya da değiştirebilirsiniz.

> [!NOTE]
> Bir uygulamanın varsayılan kültürünün kaynakları bir uydu derlemesinde da depolanabilir. Bunu yapmak için, <xref:System.Resources.NeutralResourcesLanguageAttribute> özniteliğine değerini atarsınız <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> .

## <a name="satellite-assembly-name-and-location"></a>Uydu bütünleştirilmiş kodu adı ve konumu

Hub ve bağlı bileşen modeli, kaynakların kolayca konumlandırılmaları ve kullanılması için belirli konumlara yerleştirmenizin gerekli olmasını gerektirir. Kaynakları, beklendiği gibi derleyip veya doğru konumlara yerleştirmiyorsa, ortak dil çalışma zamanı bunları bulamaz ve bunun yerine varsayılan kültürün kaynaklarını kullanır. Bir nesneyle temsil edilen .NET Framework Kaynak Yöneticisi, <xref:System.Resources.ResourceManager> yerelleştirilmiş kaynaklara otomatik olarak erişmek için kullanılır. Kaynak Yöneticisi şunları gerektirir:

- Tek bir uydu derlemesinin belirli bir kültür için tüm kaynakları içermesi gerekir. Diğer bir deyişle, birden çok *. txt* veya *. resx* dosyasını tek bir ikili *. resources* dosyasında derlemeniz gerekir.

- Bu kültürün kaynaklarını depolayan her yerelleştirilmiş kültür için uygulama dizininde ayrı bir alt dizin olmalıdır. Alt dizin adı kültür adı ile aynı olmalıdır. Alternatif olarak, uydu derlemelerinizi genel derleme önbelleğinde saklayabilirsiniz. Bu durumda, derlemenin tanımlayıcı adının kültür bilgileri bileşeni kültürünü belirtmelidir. (Bu konunun ilerleyen kısımlarında bulunan [genel derleme önbelleği bölümünde uydu derlemelerini yükleme](#SN) bölümüne bakın.)

  > [!NOTE]
  > Uygulamanız alt kültürler için kaynaklar içeriyorsa, her alt kültürü uygulama dizini altına ayrı bir alt dizine yerleştirin. Alt kültürleri ana kültürlerin dizin altındaki alt dizinlere yerleştirmeyin.

- Uydu derlemesinin uygulamayla aynı adı olması ve ".resources.dll" dosya adı uzantısını kullanması gerekir. Örneğin, bir uygulama *Example.exe*olarak adlandırılmışsa, her uydu derlemesinin adı *Example.resources.dll*olmalıdır. Uydu derleme adının, kaynak dosyalarının kültürünü belirtmediğini unutmayın. Ancak uydu derlemesi, kültürü belirten bir dizinde görüntülenir.

- Uydu derlemesinin kültürüyle ilgili bilgiler derlemenin meta verilerinde yer almalıdır. Kültür adını uydu derlemesinin meta verilerinde depolamak için, `/culture` uydu derlemesine kaynakları eklemek üzere [derleme Bağlayıcısı](../tools/al-exe-assembly-linker.md) 'nı kullandığınızda seçeneğini belirlersiniz.

Aşağıdaki çizimde, [genel derleme önbelleğine](../app-domains/gac.md)yüklememiş olduğunuz uygulamalar için örnek bir dizin yapısı ve konum gereksinimleri gösterilmektedir. . Txt ve. resources uzantılı öğeler son uygulamayla birlikte gelmez. Bunlar, son uydu kaynak derlemelerini oluşturmak için kullanılan ara kaynak dosyalarıdır. Bu örnekte,. resx dosyalarını. txt dosyaları için kullanabilirsiniz. Daha fazla bilgi için bkz. [kaynakları paketleme ve dağıtma](packaging-and-deploying-resources-in-desktop-apps.md).

Aşağıdaki görüntüde uydu derleme dizini gösterilmektedir:

![Yerelleştirilmiş kültürler alt dizinleri içeren bir uydu derleme dizini.](./media/creating-satellite-assemblies-for-desktop-apps/satellite-assembly-directory.gif)

## <a name="compiling-satellite-assemblies"></a>Uydu derlemelerini derleme

[Kaynak dosyası oluşturucuyu (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) , ikili *. resources* dosyalarına kaynakları IÇEREN metin dosyalarını veya XML (*. resx*) dosyalarını derlemek için kullanırsınız. Daha sonra, *. resources* dosyalarını uydu Derlemeleriyle derlemek Için [derleme bağlayıcısı 'nı (Al.exe)](../tools/al-exe-assembly-linker.md) kullanırsınız. *Al.exe* belirttiğiniz *. resources* dosyalarından bir derleme oluşturur. Uydu derlemeleri yalnızca kaynaklar içerebilir; herhangi bir yürütülebilir kod içeremez.

Aşağıdaki *Al.exe* komutu, Almanya kaynakları dosya dizelerinden uygulama için bir uydu derlemesi oluşturur `Example` *. de. resources*.

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll
```

Aşağıdaki *Al.exe* komutu ayrıca, uygulama için dosya dizelerinden bir uydu derlemesi oluşturur `Example` *. de. resources*. **/Template** seçeneği, uydu derlemesinin üst derlemeden (*Example.dll*) kültür bilgileri hariç tüm derleme meta verilerini devralmasını sağlar.

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll
```  
  
Aşağıdaki tabloda, bu komutlarda daha ayrıntılı olarak kullanılan *Al.exe* seçenekleri açıklanmaktadır:
  
|Seçenek|Açıklama|
|------------|-----------------|
|`-target:lib`|Uydu derlemelerinizin bir kitaplık (. dll) dosyasına derlendiğini belirtir. Bir uydu derlemesi yürütülebilir kod içermediğinden ve bir uygulamanın ana derlemesi olmadığından, uydu derlemelerini dll olarak kaydetmeniz gerekir.|
|`-embed:strings.de.resources`|Derlemeyi derlediğinde *Al.exe* eklenecek kaynak dosyasının adını belirtir. Birden çok. resources dosyasını bir uydu derlemesine ekleyebilirsiniz, ancak hub ve bağlı bileşen modelini takip ediyorsanız, her kültür için bir uydu derlemesi derlemeniz gerekir. Ancak, dizeler ve nesneler için ayrı. resources dosyaları oluşturabilirsiniz.|
|`-culture:de`|Derlenecek kaynağın kültürünü belirtir. Ortak dil çalışma zamanı, belirtilen bir kültürün kaynaklarını ararken bu bilgileri kullanır. Bu seçeneği atlarsanız *Al.exe* kaynak derlemeye devam eder, ancak çalışma zamanı bir Kullanıcı istediğinde bunu bulamaz.|
|`-out:Example.resources.dll`|Çıktı dosyasının adını belirtir. Ad, *baseName*. resources adlandırma standardını izlemelidir. *extension*, burada *baseName* , ana derlemenin adı ve *uzantısının* geçerli bir dosya adı uzantısı (. dll gibi). Çalışma zamanının, bir uydu derlemesinin, çıkış dosyası adına göre kültürünü belirleyemediğini unutmayın; belirtmek için **/Culture** seçeneğini kullanmanız gerekir.|
|`-template:Example.dll`|Uydu derlemesinin kültür alanı hariç tüm derleme meta verilerini devraldığı bir derlemeyi belirtir. Bu seçenek, yalnızca [tanımlayıcı ada](../../standard/assembly/strong-named.md)sahip bir derleme belirttiğinizde uydu derlemelerini etkiler.|
  
 *Al.exe*bulunan seçeneklerin tamamı listesi için bkz. [derleme Bağlayıcısı (Al.exe)](../tools/al-exe-assembly-linker.md).
  
## <a name="satellite-assemblies-an-example"></a>Uydu derlemeleri: bir örnek

Aşağıda yerelleştirilmiş bir selamlama içeren ileti kutusunu görüntüleyen basit bir "Hello World" örneği verilmiştir. Örnek, Ingilizce (Birleşik Devletler), Fransızca (Fransa) ve Rusça (Rusya) kültürleri için kaynakları ve geri dönüş kültürünün Ingilizce olduğunu içerir. Örneği oluşturmak için aşağıdakileri yapın:
  
1. Varsayılan kültür için kaynağı içeren *Greeting. resx* veya *Greeting.txt* adlı bir kaynak dosyası oluşturun. `HelloString`"Hello World!" olan ada sahip tek bir dizeyi depola Bu dosyada.

2. Ingilizce (en) uygulamanın varsayılan kültürünün olduğunu göstermek için, uygulamanın <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> AssemblyInfo dosyasına veya uygulamanın ana derlemesine derlenecek ana kaynak kod dosyasına aşağıdaki özniteliği ekleyin.

    [!code-csharp[Conceptual.Resources.Locating#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
    [!code-vb[Conceptual.Resources.Locating#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3. Uygulamaya aşağıdaki şekilde ek kültürler (en-US, fr-FR ve ru-RU) desteği ekleyin:  
  
    - En-US veya Ingilizce (Birleşik Devletler) kültürü desteklemek için, *Greeting. en-US. resx* veya *Greeting.en-US.txt*adlı bir kaynak dosyası oluşturun ve bunu `HelloString` değeri "Hi World!" olan tek bir dize olarak saklayın.
  
    - Fr-FR veya Fransızca (Fransa) kültürünü desteklemek için, *Greeting.fr-fr. resx* veya *Greeting.fr-FR.txt*adlı bir kaynak dosyası oluşturun ve bu adı, `HelloString` değeri "Salut tout Le Monde!" olan tek bir dize olarak depolayın.
  
    - Ru-RU veya Rusça (Rusya) kültürünü desteklemek için, *Greeting.ru-ru. resx* veya *Greeting.ru-RU.txt*adlı bir kaynak dosyası oluşturun ve bu adı, `HelloString` değeri "Всем привет!" olan tek bir dize olarak depolayın.
  
4. Her metin veya XML kaynak dosyasını bir ikili *. resources* dosyasına derlemek için [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) kullanın. Çıktı, *. resx* veya *. txt* dosyalarıyla aynı kök dosya adına sahip bir dosya kümesidir, ancak *. resources* uzantısı. Visual Studio ile örnek oluşturursanız, derleme işlemi otomatik olarak işlenir. Visual Studio kullanmıyorsanız, *. resx* dosyalarını *. resources* dosyalarına derlemek için aşağıdaki komutları çalıştırın:  
  
    ```console
    resgen Greeting.resx
    resgen Greeting.en-us.resx
    resgen Greeting.fr-FR.resx
    resgen Greeting.ru-RU.resx
    ```

    Kaynaklarınız XML dosyaları yerine metin dosyalarında ise *. resx* uzantısını *. txt*ile değiştirin.

5. Aşağıdaki kaynak kodu, uygulamanın ana derlemesinde varsayılan kültürün kaynaklarıyla birlikte derleyin:

    > [!IMPORTANT]
    > Örneği oluşturmak için Visual Studio yerine komut satırını kullanıyorsanız, <xref:System.Resources.ResourceManager> sınıf oluşturucusuna yapılan çağrıyı aşağıdaki şekilde değiştirmelisiniz:`ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`

    [!code-csharp[Conceptual.Resources.Locating#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
    [!code-vb[Conceptual.Resources.Locating#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]

    Uygulamanın adı example ise ve komut satırından derlediğiniz takdirde, C# derleyicisi için komutu şu şekilde olur:

    ```console
    csc Example.cs -res:Greeting.resources
    ```

    Karşılık gelen Visual Basic derleyici komutu:

    ```console
    vbc Example.vb -res:Greeting.resources
    ```

6. Uygulama tarafından desteklenen her yerelleştirilmiş kültür için ana uygulama dizininde bir alt dizin oluşturun. *En-US*, *fr-fr*ve *ru-ru* alt dizini oluşturmalısınız. Visual Studio bu alt dizinleri derleme sürecinin bir parçası olarak otomatik olarak oluşturur.

7. Kültüre özgü tekil *. resources* dosyalarını uydu derlemelerine ekleyin ve uygun dizine kaydedin. Her *. resources* dosyası için bunu yapmak için komutu:

    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll
    ```

     Burada *kültür* , kaynakları uydu derlemesinin içerdiği kültürün adıdır. Visual Studio bu işlemi otomatik olarak işler.

Daha sonra örneği çalıştırabilirsiniz. Bu işlem, desteklenen kültürlerin geçerli kültürden birini rastgele yapar ve yerelleştirilmiş bir selamlama görüntüler.

<a name="SN"></a>

## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a>Genel bütünleştirilmiş kod önbelleğine uydu derlemeleri yükleme

Derlemeleri yerel bir uygulama alt dizininde yüklemek yerine, bunları genel derleme önbelleğine yükleyebilirsiniz. Bu, özellikle birden çok uygulama tarafından kullanılan sınıf kitaplıkları ve sınıf kitaplığı kaynak derlemeleriniz varsa yararlıdır.
  
Derlemeleri genel bütünleştirilmiş kod önbelleğine yüklemek için tanımlayıcı adlara sahip olmaları gerekir. Tanımlayıcı adlı derlemeler geçerli bir ortak/özel anahtar çiftiyle imzalanır. Çalışma zamanının, bir bağlama isteğini karşılamak için hangi derlemeyi kullanacağını belirlemede kullandığı sürüm bilgilerini içerirler. Güçlü adlar ve sürüm oluşturma hakkında daha fazla bilgi için bkz. [derleme sürümü oluşturma](../../standard/assembly/versioning.md). Güçlü adlar hakkında daha fazla bilgi için bkz. [Strong-adlandırılmış derlemeler](../../standard/assembly/strong-named.md).

Bir uygulama geliştirirken, son ortak/özel anahtar çiftine erişiminizin olması düşüktür. Genel bütünleştirilmiş kod önbelleğine bir uydu derlemesini yüklemek ve beklendiği gibi çalıştığından emin olmak için, Gecikmeli imzalama adlı bir teknik kullanabilirsiniz. Bir derlemeyi imzalamayı ertelerseniz, derleme zamanında tanımlayıcı ad imzası için dosyada alan ayırabilirsiniz. Son ortak/özel anahtar çifti kullanılabilir olduğunda, gerçek imzalama daha sonra gecikiyor. Gecikmeli imzalama hakkında daha fazla bilgi için bkz. [bir derlemeyi IMZALAMAYı geciktirme](../../standard/assembly/delay-sign.md).

### <a name="obtaining-the-public-key"></a>Ortak anahtar alma

Bir derlemeyi imzalamayı geciktirmek için ortak anahtara erişiminizin olması gerekir. Şirketinizdeki gerçek zamanlı ortak anahtarı elde edebilir veya [tanımlayıcı ad aracını (Sn.exe)](../tools/sn-exe-strong-name-tool.md)kullanarak bir ortak anahtar oluşturabilirsiniz.

Aşağıdaki *Sn.exe* komutu bir test ortak/özel anahtar çifti oluşturur. **– K** seçeneği, *Sn.exe* yeni bir anahtar çifti oluşturup *testkeypair. snk*adlı bir dosyaya kaydetmenizi belirtir.
  
```console
sn –k TestKeyPair.snk
```

Ortak anahtarı, test anahtar çiftini içeren dosyadan ayıklayabilirsiniz. Aşağıdaki komut *Testkeypair. snk* öğesinden ortak anahtarı ayıklar ve *PublicKey. snk*içine kaydeder:

```console
sn –p TestKeyPair.snk PublicKey.snk
```

### <a name="delay-signing-an-assembly"></a>Derleme İmzalamayı Geciktirme

Ortak anahtarı aldıktan veya oluşturduktan sonra, derlemeyi derlemek ve Gecikmeli imzalamayı belirtmek için [Derleme Bağlayıcı (Al.exe)](../tools/al-exe-assembly-linker.md) kullanın.

Aşağıdaki *Al.exe* komutu, *dizeler. ja. resources* dosyasından uygulama StringLibrary için tanımlayıcı adlı bir uydu derlemesi oluşturur:

```console
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk
```

**-Delay +** seçeneği, derleme bağlayıcının derlemeyi imzalamasını geciktirmesi gerektiğini belirtir. **-Keyfile** seçeneği, derlemeyi imzalamayı geciktirmede kullanılacak ortak anahtarı içeren anahtar dosyasının adını belirtir.

### <a name="re-signing-an-assembly"></a>Derlemeyi yeniden imzalama

Uygulamanızı dağıtmadan önce, gecikmeli imzalanmış uydu derlemesini gerçek anahtar çiftiyle yeniden imzalamanız gerekir. Bunu *Sn.exe*kullanarak yapabilirsiniz.

Aşağıdaki *Sn.exe* komutu, *RealKeyPair. snk*dosyasında depolanan anahtar çiftiyle *StringLibrary.resources.dll* imzalar. **– R** seçeneği, önceden imzalanmış veya gecikmeli imzalanmış bir derlemenin yeniden imzalanıp imzalanmadığını belirtir.

```console
sn –R StringLibrary.resources.dll RealKeyPair.snk
```

### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a>Genel bütünleştirilmiş kod önbelleğine uydu derlemesi yükleme

Çalışma zamanı, kaynak geri dönüş işlemindeki kaynakları aradığında, önce [genel derleme önbelleğine](../app-domains/gac.md) bakar. (Daha fazla bilgi için [kaynakları paketleme ve dağıtma](packaging-and-deploying-resources-in-desktop-apps.md) konusunun "kaynak geri dönüş işlemi" bölümüne bakın.) Uydu bütünleştirilmiş kodu bir tanımlayıcı ad ile imzalandığı anda, [genel bütünleştirilmiş kod önbelleği aracı (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md)kullanılarak genel derleme önbelleğine yüklenebilir.

Aşağıdaki *Gacutil.exe* komutu, genel derleme önbelleğinde *StringLibrary.resources.dll** ' i yüklüyor:

```console
gacutil -i:StringLibrary.resources.dll
```

**/İ** seçeneği *Gacutil.exe* belirtilen derlemeyi genel derleme önbelleğine yüklemesi gerektiğini belirtir. Uydu derlemesi önbellekte yüklendikten sonra, içerdiği kaynaklar uydu derlemesini kullanacak şekilde tasarlanan tüm uygulamalar tarafından kullanılabilir hale gelir.

### <a name="resources-in-the-global-assembly-cache-an-example"></a>Genel derleme önbelleğindeki kaynaklar: bir örnek

Aşağıdaki örnek, bir kaynak dosyasından yerelleştirilmiş bir karşılama ayıklamak ve döndürmek için .NET Framework sınıf kitaplığındaki bir yöntemi kullanır. Kitaplık ve kaynakları genel derleme önbelleğine kaydedilir. Örnek, Ingilizce (Birleşik Devletler), Fransızca (Fransa), Rusça (Rusya) ve Ingilizce kültürlerin kaynaklarını içerir. Varsayılan kültür İngilizce 'dir; kaynakları ana derlemede depolanır. Örnek Başlangıçta, kitaplığı ve uydu derlemelerini ortak anahtarla imzalar ve sonra bunları ortak/özel anahtar çifti ile yeniden imzalar. Örneği oluşturmak için aşağıdakileri yapın:

1. Visual Studio kullanmıyorsanız, *Reskey. snk*adlı bir ortak/özel anahtar çifti oluşturmak Için aşağıdaki [tanımlayıcı ad Aracı (Sn.exe)](../tools/sn-exe-strong-name-tool.md) komutunu kullanın:

    ```console
    sn –k ResKey.snk
    ```

    Visual Studio kullanıyorsanız, anahtar dosyasını oluşturmak için proje **özellikleri** Iletişim kutusunun **imzalama** sekmesini kullanın.

2. *PublicKey. snk*adlı bir ortak anahtar dosyası oluşturmak Için aşağıdaki [tanımlayıcı ad Aracı (Sn.exe)](../tools/sn-exe-strong-name-tool.md) komutunu kullanın:

    ```console
    sn –p ResKey.snk PublicKey.snk
    ```

3. Varsayılan kültür için kaynağı içerecek *dizeler. resx* adlı bir kaynak dosyası oluşturun. `Greeting`"Değeri" nasıl yapılır? "adlı tek bir dizeyi depola Bu dosyada.

4. "En" ın uygulamanın varsayılan kültürü olduğunu belirtmek için, uygulamanın <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> AssemblyInfo dosyasına veya uygulamanın ana derlemesine derlenecek ana kaynak kod dosyasına aşağıdaki özniteliği ekleyin:

    [!code-csharp[Conceptual.Resources.Satellites#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
    [!code-vb[Conceptual.Resources.Satellites#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]

5. Uygulamaya ek kültürler (en-US, fr-FR ve ru-RU kültürleri) için aşağıdaki şekilde bir destek ekleyin:

    - "En-US" veya Ingilizce (Birleşik Devletler) kültürünü desteklemek için, *dizeler. en-US. resx* veya *Strings.en-US.txt*adlı bir kaynak dosyası oluşturun ve bu adı, `Greeting` değeri "Hello!" olan tek bir dize içinde saklayın.

    - "Fr-FR" veya Fransızca (Fransa) kültürünü desteklemek için, *Strings.fr-fr. resx* veya *Strings.fr-FR.txt* adlı bir kaynak dosyası oluşturun ve bunu `Greeting` değeri "iyi jour!" olan tek bir dize olarak saklayın.

    - "Ru-RU" veya Rusça (Rusya) kültürünü desteklemek için, *Strings.ru-ru. resx* veya *Strings.ru-RU.txt* adlı bir kaynak dosyası oluşturun ve bu `Greeting` değeri "привет!" olan adlı tek bir dize olarak depolayın.

6. Her metin veya XML kaynak dosyasını bir ikili. resources dosyasına derlemek için [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) kullanın. Çıktı, *. resx* veya *. txt* dosyalarıyla aynı kök dosya adına sahip bir dosya kümesidir, ancak *. resources* uzantısı. Visual Studio ile örnek oluşturursanız, derleme işlemi otomatik olarak işlenir. Visual Studio kullanmıyorsanız, *. resx* dosyalarını *. resources* dosyalarına derlemek için aşağıdaki komutu çalıştırın:

    ```console
    resgen filename
    ```

    Burada *Dosya* adı, *. resx* veya metin dosyasının uzantısı olan isteğe bağlı yoldur.

7. *StringLibrary. vb* veya *StringLibrary.cs* için aşağıdaki kaynak kodu, varsayılan kültürün kaynaklarıyla birlikte *StringLibrary.dll*adlı gecikmeli imzalanmış bir kitaplık derlemesine derleyin:

    > [!IMPORTANT]
    > Örneği oluşturmak için Visual Studio yerine komut satırını kullanıyorsanız, <xref:System.Resources.ResourceManager> sınıf oluşturucusuna olan çağrıyı olarak değiştirmelisiniz `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);` .

    [!code-csharp[Conceptual.Resources.Satellites#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
    [!code-vb[Conceptual.Resources.Satellites#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]

    C# derleyicisi için komutu:

    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs
    ```

    Karşılık gelen Visual Basic derleyici komutu:

    ```console
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb
    ```

8. Uygulama tarafından desteklenen her yerelleştirilmiş kültür için ana uygulama dizininde bir alt dizin oluşturun. *En-US*, *fr-fr*ve *ru-ru* alt dizini oluşturmalısınız. Visual Studio bu alt dizinleri derleme sürecinin bir parçası olarak otomatik olarak oluşturur. Tüm uydu derlemeleri aynı dosya adına sahip olduğundan, ortak/özel anahtar çifti ile imzalanana kadar kültüre özgü ayrı uydu derlemelerini depolamak için alt dizinler kullanılır.

9. Kültüre özgü bağımsız *. resources* dosyalarını gecikmeli imzalanmış uydu derlemelerine katıştırın ve uygun dizine kaydedin. Her *. resources* dosyası için bunu yapmak için komutu:

    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk
    ```

    Burada *kültür* bir kültürün adıdır. Bu örnekte, kültür adları en-US, fr-FR ve ru-RU ' dir.

10. *StringLibrary.dll* [tanımlayıcı ad Aracı (Sn.exe)](../tools/sn-exe-strong-name-tool.md) kullanarak aşağıdaki şekilde yeniden imzalayın:

    ```console
    sn –R StringLibrary.dll RealKeyPair.snk
    ```

11. Tek tek uydu derlemelerini yeniden imzalayın. Bunu yapmak için, her uydu derlemesi için aşağıdaki gibi [tanımlayıcı ad aracını (Sn.exe)](../tools/sn-exe-strong-name-tool.md) kullanın:

    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk
    ```

12. Aşağıdaki komutu kullanarak genel derleme önbelleğindeki *StringLibrary.dll* ve her bir uydu derlemesini kaydedin:

    ```console
    gacutil -i filename
    ```

    Burada *filename* , kayıt yapılacak dosyanın adıdır.

13. Visual Studio kullanıyorsanız, adlı yeni bir **konsol uygulaması** projesi oluşturun `Example` , *StringLibrary.dll* ve aşağıdaki kaynak koda bir başvuru ekleyin ve derleyin.

    [!code-csharp[Conceptual.Resources.Satellites#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
    [!code-vb[Conceptual.Resources.Satellites#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]

    Komut satırından derlemek için, C# derleyicisi için aşağıdaki komutu kullanın:

    ```console
    csc Example.cs -r:StringLibrary.dll
    ```

    Visual Basic Derleyicisi için komut satırı:

    ```console
    vbc Example.vb -r:StringLibrary.dll
    ```

14. *Example.exe*çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Kaynakları Paketleme ve Dağıtma](packaging-and-deploying-resources-in-desktop-apps.md)
- [Bütünleştirilmiş Kod İmzalamayı Geciktirme](../../standard/assembly/delay-sign.md)
- [Al.exe (bütünleştirilmiş kod bağlayıcı)](../tools/al-exe-assembly-linker.md)
- [Sn.exe (tanımlayıcı ad aracı)](../tools/sn-exe-strong-name-tool.md)
- [Gacutil.exe (Genel Bütünleştirilmiş Kod Önbelleği Aracı)](../tools/gacutil-exe-gac-tool.md)
- [Masaüstü uygulamalarındaki kaynaklar](index.md)
