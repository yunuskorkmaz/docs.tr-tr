---
title: Mpgo.exe (Yönetilen Profil Temelli İyileştirme Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Mpgo.exe
- training scenarios, generating profiles with
- Managed Profile Guided Optimization Tool
- Ngen.exe
- Ngen.exe, profilers and native images
ms.assetid: f6976502-a000-4fbe-aaf5-a7aab9ce4ec2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e72e091d9b120042254df5de323169f6f67c61d4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616066"
---
# <a name="mpgoexe-managed-profile-guided-optimization-tool"></a>Mpgo.exe (Yönetilen Profil Temelli İyileştirme Aracı)

Yönetilen profil Kılavuzlu optimizasyon Aracı (Mpgo.exe) tarafından oluşturulan yerel görüntü derlemelerini en iyi duruma getirmek için son kullanıcı senaryoları kullanan bir komut satırı aracıdır [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md). Bu araç, profil verilerini oluşturan eğitim senaryolarını çalıştırmanızı sağlar. [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) oluşturulan yerel görüntü uygulama derlemelerini en iyi duruma getirmek için bu verileri kullanır. Eğitim senaryosu, uygulamanızın beklenen bir kullanımına ilişkin denemedir. Mpgo.exe, Visual Studio Ultimate 2012 ve sonraki sürümlerinde kullanılabilir. Visual Studio 2013 ile başlayarak, ayrıca Mpgo.exe en iyi duruma getirmek için kullanabileceğiniz [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.  
  
Profil destekli en iyi duruma getirme süreci, eğitim senaryolarından veri toplayıp yerel görüntülerin düzenini en iyi duruma getirmek üzere onları kullanarak verimi, bellek kullanımını (çalışma kümesi boyutu) ve uygulama başlatma süresini iyileştirir.  
  
Ara Dil (IL) derlemeleri için başlatma süresi ve çalışma kümesi boyutuyla ilgili performansı sorunlarıyla karşılaştığınızda, just-in-time (JIT) (tam zamanında) derleme maliyetlerini ortadan kaldırmak ve kod paylaşımını kolaylaştırmak için ilk Ngen.exe'yi kullanmanızı öneririz. Ek geliştirmeler gerekiyorsa, uygulamanızı daha ileri düzeyde iyi hale getirmek etmek için Mpgo.exe kullanabilirsiniz. Performans artışlarını değerlendirmek için temel olarak, en iyi duruma getirilmemiş yerel görüntü derlemelerindeki performans verilerini kullanabilirsiniz. Mpgo.exe kullanıldığında soğuk başlangıç sürelerinde kısalma ve çalışma kümesi boyutunda azalma görülebilir. Mpgo.exe, en iyi duruma getirilmiş yerel görüntü derlemeleri oluşturmak için Ngen.exe'yi kullanan IL derlemelerine bilgi ekler. Daha fazla bilgi için bkz: Giriş [Masaüstü uygulamaları için başlatma performansını iyileştirme](https://go.microsoft.com/fwlink/p/?LinkId=248943) .NET blogunda.  
  
Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için yönetici kimlik bilgileriyle Visual Studio (veya Windows 7'de Visual Studio komut istemi) için geliştirici komut istemi kullanın ve komut isteminde aşağıdaki komutu yazın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
Masaüstü uygulamaları için:  
  
```  
mpgo –Scenario <command> [-Import <directory>] –AssemblyList <assembly1>  <assembly2> ... -OutDir <directory> [options]  
```  
  
İçin [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
mpgo –Scenario <packageName> -AppID <appId> -Timeout <seconds>  
```  
  
## <a name="parameters"></a>Parametreler  
 Mpgo.exe için tüm bağımsız değişkenler büyük/küçük harfe duyarsızdır. Komutlara önek olarak bir tire işareti eklenir.  
  
> [!NOTE]
> Kullanabilirsiniz `–Scenario` veya `–Import` olarak gerekli komutu, ancak ikisine birden değil. Belirtirseniz gerekli parametrelerin hiçbiri kullanılan `–Reset` seçeneği.

|Gerekli parametre|Açıklama|
|------------------------|-----------------|
|`-Scenario` \<*Komutu*><br /><br /> —veya—<br /><br /> `-Scenario` \<*Paket adı*><br /><br /> -veya-<br /><br /> `-Import` \<*Dizin*>|Masaüstü uygulamaları için kullanmayı `–Scenario` istediğiniz iyileştirmek, herhangi bir komut satırı bağımsız değişkeni de dahil olmak üzere uygulamayı çalıştırmak için komutu belirtmek için. Üç adet çift tırnak işaretleri, *komut* ; boşluk içeren bir yol belirtiyorsa, örneğin: `mpgo.exe -scenario """C:\My App\myapp.exe""" -assemblylist """C:\My App\myapp.exe""" -outdir "C:\optimized files"`. Çift tırnak işareti kullanmayın; Bunlar düzgün çalışmaz *komut* alanları içerir.<br /><br /> -veya-<br /><br /> İçin [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları, `–Scenario` için profil bilgilerini oluşturmak istediğiniz paketi belirtmek için. Tam paket adı yerine, paketin görünen adını veya paket aile adını belirtirseniz ve yalnızca tek bir eşleşme varsa Mpgo.exe sağladığınız adla eşleşen paketi seçer. Belirtilen adla eşleşen birden çok paket varsa, Mpgo.exe sizden bir paket seçmenizi ister.<br /><br /> —veya—<br /><br /> Kullanım `-Import` getirme belirtmek için daha önce en iyi duruma getirilmiş derlemeleri verilerden derlemelerde iyileştirmek için kullanılması gereken `-AssemblyList`. *Dizin* , daha önce en iyi duruma getirilmiş dosyaları içeren dizini belirtir. İçinde belirtilen derlemeler `–AssemblyList` veya `–AssemblyListFile` içe aktarılan dosyalara ait veriler kullanılarak en iyi duruma getirilecek derlemelerin yeni sürümleridir. Derlemelerin eski sürümlerine ait en iyi duruma getirme verilerini kullanmak, senaryoyu yeniden çalıştırmadan derlemelerin yeni sürümlerini en iyi duruma getirmenizi sağlar.  Ancak, içe aktarılan ve hedef derlemeler önemli ölçüde farklı kodlar içeriyorsa, en iyi duruma getirme verileri etkisiz olur. Belirtilen derleme adları `–AssemblyList` veya `–AssemblyListFile` tarafından belirtilen dizinde bulunmalıdır `–Import` *dizin*. Üç adet çift tırnak işaretleri, *dizin* boşluklar içeren bir yol belirtir.<br /><br /> Belirtmeli `–Scenario` veya `–Import`, ancak parametrelerinin ikisi birden değil.|
|`-OutDir` \<*Dizin*>|En iyi duruma getirilmiş derlemelerin yerleştirileceği dizin. Çıktı dizini klasöründe bir derleme zaten varsa, yeni bir kopya oluşturulur ve adının bir dizin numarası eklenir; Örneğin: *assemblyname*-1.exe. Çift tırnak işaretleri içine alın *dizin* boşluk içeren bir yol belirtir.|
|`-AssemblyList` \<*assembly1 assembly2...*><br /><br /> —veya—<br /><br /> `-AssemblyListFile` \<*Dosya*>|Hakkında profil bilgileri toplamak istediğiniz derlemeleri (.exe ve .dll dosyaları gibi) boşluklarla ayrılmış olarak içeren bir liste. Belirtebileceğiniz `C:\Dir\*.dll` veya `*.dll` atanmış veya geçerli çalışma dizininde tüm derlemeleri seçin. Daha fazla bilgi için Açıklamalar bölümüne bakın.<br /><br /> —veya—<br /><br /> Her satırda bir derleme olacak şekilde, hakkında profil bilgileri toplamak istediğiniz derlemelerin listesini içeren bir metin dosyası. Bir derleme adı tire işareti (-) ile başlıyorsa, bir derleme dosyası listesi kullanın veya derlemeyi yeniden adlandırın.|
|`-AppID` \<*appId*>|Belirtilen paketteki uygulamanın kimliği. Joker karakter kullanıyorsanız (\*), Mpgo.exe paketteki uygulama kimliklerini numaralandırmayı deneyecek ve \< *package_family_name*>! Başarısız olursa uygulama. Başında önek olarak ünlem işareti (!) konmuş bir dize belirtirseniz, Mpgo.exe paket aile adını sağlanan bağımsız değişkenle birleştirir.|
|`-Timeout` \<*saniye*>|İzin vermek için süreyi [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamasının uygulama çıkışından önce çalışmasına.|

|İsteğe bağlı parametre|Açıklama|
|------------------------|-----------------|
|`-64bit`|64-bit sistemler için derlemeleri kullanır.  Derlemeniz kendisini 64-bit olarak bildiriyor olsa da 64-bit derlemeler için bu parametreyi belirtmelisiniz.|
|`-ExeConfig` \<*Dosya adı*>|Senaryonuzun sürüm ve yükleyici bilgilerini sağlamak üzere kullandığı yapılandırma dosyasını belirtir.|
|`-f`|İmzalanmış olsa da, ikili bir derlemeye profil verilerinin eklenmesini sağlar.  Derleme imzalanmışsa, yeniden imzalanması gerekir; aksi takdirde derleme yüklenemez ve çalıştırılamaz.|
|`-Reset`|İptal edilen bir profil oluşturma oturumunun derlemelerinizi etkilemediğinden emin olmak için ortamı sıfırlar ve ardından çıkış yapar. Ortam varsayılan olarak bir profil oluşturma oturumundan önce ve sonra sıfırlanır.|
|`-Timeout` \<*saniye cinsinden süre*>|Profil oluşturma süresini saniye cinsinden belirtir. GUI uygulamaları için, gözlemlenen başlangıç zamanlarınızdan biraz daha büyük bir değer kullanın. Uygulama çalışmaya devam etse de, zaman aşımı süresinin sonunda profil verileri kaydedilir. Bu seçeneği ayarlamazsanız, profil oluşturma işlemi uygulamayı kapanana kadar devam eder, ardından veriler kaydedilir.|
|`-LeaveNativeImages`|Kullanılan yerel görüntülerin senaryo çalıştırıldıktan sonra kaldırılmayacağını belirtir. Bu seçenek öncelikle senaryo için belirttiğiniz uygulamayı çalıştırırken kullanılır. Mpgo.exe'nin sonraki çalışmaları için yerel görüntülerin yeniden oluşturulmasını önler. Bu seçeneği belirtirseniz, uygulamanızı çalıştırmayı tamamladığınızda, önbellekte üst öğesi olmayan yerel görüntüler olabilir. Bu durumda, aynı senaryo ve derleme listesiyle Mpgo.exe'yi çalıştırın ve kullanma `–RemoveNativeImages` bu yerel görüntüleri kaldırmak için parametre.|
|`-RemoveNativeImages`|Bir çalıştırma işleminden temizler burada `–LeaveNativeImages` belirtildi. Belirtirseniz `-RemoveNativeImages`, Mpgo.exe dışında herhangi bir bağımsız değişken yok sayar `-64bit` ve `–AssemblyList`ve kullanılan yerel görüntülerin tümünü kaldırdıktan sonra çıkış yapar.|

## <a name="remarks"></a>Açıklamalar
 Her ikisi de kullanabileceğiniz `–AssemblyList` ve `- AssemblyListFile` birden çok kez komut satırında.

 Derlemeleri belirtirken tam yol adları belirtmezseniz, Mpgo.exe geçerli dizinde arar. Yanlış bir yol belirtirseniz, Mpgo.exe bir hata iletisi görüntüler, ancak diğer derlemeler için veri oluşturmaya devam eder. Eğitim senaryosu sırasında yüklenmemiş bir derleme belirtirseniz, o derleme için eğitim verisi oluşturulmaz.

 Listedeki bir derleme genel derleme önbelleğinde ise, profil bilgilerini içerecek şekilde güncelleştirilmez.  Profil bilgilerini toplamak için onu genel derleme önbelleğinden kaldırın.

 Ngen.exe ve Mpgo.exe'nin kullanılması yalnızca yönetilen büyük uygulamalar için önerilir, çünkü önceden derlenmiş yerel görüntülerin yararı genellikle yalnızca çalışma zamanında önemli ölçüde JIT derlemesini kaldırdığında görülür. Mpgo.exe çalışma kümesi yoğun olmayan "Merhaba Dünya" tarzı uygulamalarda mpgo.exe'yi çalıştırmak herhangi bir avantaj sağlamaz ve Mpgo.exe profil verilerini toplamak bile başarısız olabilir.

> [!NOTE]
> Ngen.exe ve Mpgo.exe, ASP.NET uygulamaları ve Windows Communication Foundation (WCF) hizmetleri için önerilmez.  
  
## <a name="to-use-mpgoexe"></a>Mpgo.exe'yi kullanmak için  
  
1. Visual Studio Ultimate 2012 ve uygulamanızın yüklü olduğu bir bilgisayar kullanın.  
  
2. Mpgo.exe'yi bir yönetici olarak gerekli parametrelerle çalıştırın.  Örnek komutlar için sonraki bölüme bakın.  
  
     En iyi duruma getirilmiş Ara dil (IL) derlemeleri tarafından belirtilen klasörde oluşturulan `–OutDir` parametre (Bu örneklerde, `C:\Optimized` klasörü).  
  
3. Tarafından belirtilen dizindeki profil bilgilerini içeren yeni IL derlemeleriyle ile Ngen.exe için kullandığınız IL derlemelerini değiştirin `–OutDir`.  
  
4. Mpgo.exe tarafından sağlanan görüntüleri kullanan uygulama kurulumu en iyi duruma getirilmiş yerel görüntüleri yükler.  
  
## <a name="suggested-workflow"></a>Önerilen İş Akışı  
  
1. Mpgo.exe'yi kullanarak bir dizi en iyi duruma getirilmiş IL derlemeleri oluşturun `–Scenario` parametresi.  
  
2. En iyi duruma getirilmiş IL derlemelerini kaynak denetime girin.  
  
3. Derleme işleminde ile Mpgo.exe'yi çağırın `–Import` parametre oluşturmak için oluşturma sonrası adımı olarak en iyi duruma getirilmiş IL görüntüleri Ngen.exe'ye geçirilecek.  
  
 Bu işlem tüm derlemelerin en iyi duruma getirilmiş verilere sahip olmasını sağlar. Güncelleştirilmiş en iyi duruma getirilmiş derlemeleri daha sık iade ederseniz (1. ve 2. adım), tüm üretim geliştirme sürecinde performans numaraları daha tutarlı olur.  
  
## <a name="using-mpgoexe-from-visual-studio"></a>Visual Studio'dan Mpgo.exe'yi kullanma  
 Mpgo.exe Visual Studio'dan çalıştırabilirsiniz (bkz [nasıl yapılır: Derleme olayları belirtme (C#)](/visualstudio/ide/how-to-specify-build-events-csharp)) aşağıdaki kısıtlamalarla:  
  
- Visual Studio makroları aynı zamanda varsayılan olarak sonlarında eğik çizgiler içerdiğinden, sonda eğik çizgileri olan tırnak işaretli yollar kullanamazsınız. (Örneğin, `–OutDir "C:\Output Folder\"` geçersiz.) Bu kısıtlamayı çözmek için sondaki eğik çizgilerden kaçınabilirsiniz. (Örneğin, `-OutDir "$(OutDir)\"` yerine.)  
  
- Varsayılan olarak, Mpgo.exe Visual Studio yapı yolu üzerinde değildir. Yolu Visual Studio'ya eklemeli ya da Mpgo komut satırında tam yolu belirtmelisiniz. Kullanabilirsiniz `–Scenario` veya `–Import` Visual Studio'da oluşturma sonrası olay parametresi. Ancak, tipik işlem kullanmaktır `–Scenario` bir kez bir geliştirici komut istemi için Visual Studio ve ardından `–Import` her yapıdan sonra; en iyi duruma getirilmiş derlemeleri güncelleştirmek için örneğin: `"C:\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\mpgo.exe" -import "$(OutDir)tmp" -assemblylist "$(TargetPath)" -outdir "$(OutDir)\"`.  
  
<a name="samples"></a>   
## <a name="examples"></a>Örnekler  
 Visual Studio için geliştirici komut istemi gelen aşağıdaki Mpgo.exe komutu bir vergi uygulamasını en iyi duruma getirir:  
  
```  
mpgo –scenario "C:\MyApp\MyTax.exe /params par" –AssemblyList Mytax.dll MyTaxUtil2011.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 Aşağıdaki Mpgo.exe komut bir ses uygulamasını en iyi duruma getirir:  
  
```  
mpgo –scenario "C:\MyApp\wav2wma.exe –input song1.wav –output song1.wma" –AssemblyList transcode.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 Aşağıdaki Mpgo.exe komutu yeni sürümleri en iyi duruma getirmek için daha önce en iyi duruma getirilmiş derlemelere ait verileri kullanır:  
  
```  
mpgo.exe -import "C:\Optimized" -assemblylist "C:\MyApp\MyTax.dll" "C:\MyApp\MyTaxUtil2011.dll" -outdir C:\ReOptimized  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ngen.exe (Yerel Görüntü Oluşturucu)](../../../docs/framework/tools/ngen-exe-native-image-generator.md)
- [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
- [Masaüstü uygulamaları için başlatma performansını iyileştirme](https://go.microsoft.com/fwlink/p/?LinkId=248943)
- [.NET 4.5 performans geliştirmeleri genel bakış](https://go.microsoft.com/fwlink/p/?LinkId=249131)
