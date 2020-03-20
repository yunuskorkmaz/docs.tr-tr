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
ms.openlocfilehash: 0052475697dae2c3ad891db18d300b5ec08a7e62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180342"
---
# <a name="mpgoexe-managed-profile-guided-optimization-tool"></a>Mpgo.exe (Yönetilen Profil Temelli İyileştirme Aracı)

Yönetilen Profil Kılavuzlu Optimizasyon Aracı (Mpgo.exe), [Yerel Görüntü Oluşturucusu (Ngen.exe)](ngen-exe-native-image-generator.md)tarafından oluşturulan yerel görüntü derlemelerini optimize etmek için ortak son kullanıcı senaryolarını kullanan bir komut satırı aracıdır. Bu araç, profil verilerini oluşturan eğitim senaryolarını çalıştırmanızı sağlar. [Yerel Görüntü Oluşturucusu (Ngen.exe),](ngen-exe-native-image-generator.md) oluşturulan yerel görüntü uygulama derlemelerini optimize etmek için bu verileri kullanır. Eğitim senaryosu, uygulamanızın beklenen bir kullanımına ilişkin denemedir. Mpgo.exe, Visual Studio Ultimate 2012 ve sonraki sürümlerinde kullanılabilir. Visual Studio 2013'ten başlayarak, Windows 8.x Store uygulamalarını optimize etmek için Mpgo.exe'yi de kullanabilirsiniz.  
  
Profil destekli en iyi duruma getirme süreci, eğitim senaryolarından veri toplayıp yerel görüntülerin düzenini en iyi duruma getirmek üzere onları kullanarak verimi, bellek kullanımını (çalışma kümesi boyutu) ve uygulama başlatma süresini iyileştirir.  
  
Ara Dil (IL) derlemeleri için başlatma süresi ve çalışma kümesi boyutuyla ilgili performansı sorunlarıyla karşılaştığınızda, just-in-time (JIT) (tam zamanında) derleme maliyetlerini ortadan kaldırmak ve kod paylaşımını kolaylaştırmak için ilk Ngen.exe'yi kullanmanızı öneririz. Ek geliştirmeler gerekiyorsa, uygulamanızı daha ileri düzeyde iyi hale getirmek etmek için Mpgo.exe kullanabilirsiniz. Performans artışlarını değerlendirmek için temel olarak, en iyi duruma getirilmemiş yerel görüntü derlemelerindeki performans verilerini kullanabilirsiniz. Mpgo.exe kullanıldığında soğuk başlangıç sürelerinde kısalma ve çalışma kümesi boyutunda azalma görülebilir. Mpgo.exe, en iyi duruma getirilmiş yerel görüntü derlemeleri oluşturmak için Ngen.exe'yi kullanan IL derlemelerine bilgi ekler. Daha fazla bilgi için ,.NET blogunda [Masaüstü Uygulamalarınız için Başlatma Performansını Artırma](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/) girişine bakın.  
  
Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7) with administrator credentials, and type the following at the command prompt. Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.  
  
Masaüstü uygulamaları için:  
  
```console  
mpgo –Scenario <command> [-Import <directory>] –AssemblyList <assembly1>  <assembly2> ... -OutDir <directory> [options]  
```  
  
Windows 8.x Store uygulamaları için:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
mpgo –Scenario <packageName> -AppID <appId> -Timeout <seconds>  
```  
  
## <a name="parameters"></a>Parametreler  
 Mpgo.exe için tüm bağımsız değişkenler büyük/küçük harfe duyarsızdır. Komutlara önek olarak bir tire işareti eklenir.  
  
> [!NOTE]
> Gerekli komut `–Scenario` olarak `–Import` veya her ikisini de kullanamazsınız. Seçeneği belirtirseniz gerekli parametrelerin `–Reset` hiçbiri kullanılmaz.

|Gerekli parametre|Açıklama|
|------------------------|-----------------|
|`-Scenario`\< *komutu*><br /><br /> —veya—<br /><br /> `-Scenario`\< *paketAdı*><br /><br /> -veya-<br /><br /> `-Import`\< *dizin*>|Masaüstü uygulamaları için, komut satırı bağımsız değişkenleri de dahil olmak üzere en iyi duruma getirmek istediğiniz uygulamayı çalıştırmak için komutu belirtmeyi kullanın. `–Scenario` Boşluk içeren bir yol belirtinse, *komut* etrafında üç çift tırnak işareti kümesi kullanın; örneğin: `mpgo.exe -scenario """C:\My App\myapp.exe""" -assemblylist """C:\My App\myapp.exe""" -outdir "C:\optimized files"`. Çift tırnak işaretleri kullanmayın; *komut* boşlukları içeriyorsa, bunlar doğru çalışmaz.<br /><br /> -veya-<br /><br /> Windows 8.x Store uygulamaları `–Scenario` için profil bilgileri oluşturmak istediğiniz paketi belirtmek için kullanın. Tam paket adı yerine, paketin görünen adını veya paket aile adını belirtirseniz ve yalnızca tek bir eşleşme varsa Mpgo.exe sağladığınız adla eşleşen paketi seçer. Belirtilen adla eşleşen birden çok paket varsa, Mpgo.exe sizden bir paket seçmenizi ister.<br /><br /> —veya—<br /><br /> Daha `-Import` önce optimize edilmiş derlemelerden en iyi duruma getirme verilerinin , `-AssemblyList`'deki derlemeleri en iyi duruma getirmek için kullanılması gerektiğini belirtmek için kullanın. *dizin,* daha önce en iyi duruma getirilmiş dosyaları içeren dizin belirtir. Alınan dosyalardaki `–AssemblyList` veriler `–AssemblyListFile` kullanılarak en iyi duruma getirilecek derlemelerde belirtilen veya yeni sürümleri olan derlemeler. Derlemelerin eski sürümlerine ait en iyi duruma getirme verilerini kullanmak, senaryoyu yeniden çalıştırmadan derlemelerin yeni sürümlerini en iyi duruma getirmenizi sağlar.  Ancak, içe aktarılan ve hedef derlemeler önemli ölçüde farklı kodlar içeriyorsa, en iyi duruma getirme verileri etkisiz olur. Dizinde `–AssemblyList` belirtilen veya `–AssemblyListFile` `–Import` *dizin*içinde yer alması gereken montaj adları. Boşluk içeren bir yol belirtse, *dizinin* etrafında üç çift tırnak işareti kümesi kullanın.<br /><br /> Her iki `–Scenario` parametreyi belirtmeniz gerekir, `–Import`ancak her iki parametreyi belirtmemelisiniz.|
|`-OutDir`\< *dizin*>|En iyi duruma getirilmiş derlemelerin yerleştirileceği dizin. Çıktı dizini klasöründe zaten bir derleme varsa, yeni bir kopya oluşturulur ve adına bir dizin numarası eklenir; örneğin: *assemblyname*-1.exe. Boşluk içeren bir yol belirtse *dizinin* etrafındaki çift tırnak işaretlerini kullanın.|
|`-AssemblyList`\< *assembly1 assembly2 ...*><br /><br /> —veya—<br /><br /> `-AssemblyListFile`\< *dosya*>|Hakkında profil bilgileri toplamak istediğiniz derlemeleri (.exe ve .dll dosyaları gibi) boşluklarla ayrılmış olarak içeren bir liste. Belirlenen veya `C:\Dir\*.dll` `*.dll` geçerli çalışma dizinindeki tüm derlemeleri belirtebilir veya seçebilirsiniz. Daha fazla bilgi için Açıklamalar bölümüne bakın.<br /><br /> —veya—<br /><br /> Her satırda bir derleme olacak şekilde, hakkında profil bilgileri toplamak istediğiniz derlemelerin listesini içeren bir metin dosyası. Bir derleme adı tire işareti (-) ile başlıyorsa, bir derleme dosyası listesi kullanın veya derlemeyi yeniden adlandırın.|
|`-AppID`\< *appId*>|Belirtilen paketteki uygulamanın kimliği. Eğer joker kullanırsanız\*( ), Mpgo.exe paketteki AppId'leri sayısallaştırmaya çalışacak ve \< *package_family_name*> geri düşecek! Başarısız olursa uygulama. Başında önek olarak ünlem işareti (!) konmuş bir dize belirtirseniz, Mpgo.exe paket aile adını sağlanan bağımsız değişkenle birleştirir.|
|`-Timeout`\< *saniye*>|Windows 8.x Store uygulamasının uygulama çıkmadan önce çalışmasına izin verme süresi.|

|İsteğe bağlı parametre|Açıklama|
|------------------------|-----------------|
|`-64bit`|64-bit sistemler için derlemeleri kullanır.  Derlemeniz kendisini 64-bit olarak bildiriyor olsa da 64-bit derlemeler için bu parametreyi belirtmelisiniz.|
|`-ExeConfig`\< *dosya adı*>|Senaryonuzun sürüm ve yükleyici bilgilerini sağlamak üzere kullandığı yapılandırma dosyasını belirtir.|
|`-f`|İmzalanmış olsa da, ikili bir derlemeye profil verilerinin eklenmesini sağlar.  Derleme imzalanmışsa, yeniden imzalanması gerekir; aksi takdirde derleme yüklenemez ve çalıştırılamaz.|
|`-Reset`|İptal edilen bir profil oluşturma oturumunun derlemelerinizi etkilemediğinden emin olmak için ortamı sıfırlar ve ardından çıkış yapar. Ortam varsayılan olarak bir profil oluşturma oturumundan önce ve sonra sıfırlanır.|
|`-Timeout`\< *saniye cinsinden zaman*>|Profil oluşturma süresini saniye cinsinden belirtir. GUI uygulamaları için, gözlemlenen başlangıç zamanlarınızdan biraz daha büyük bir değer kullanın. Uygulama çalışmaya devam etse de, zaman aşımı süresinin sonunda profil verileri kaydedilir. Bu seçeneği ayarlamazsanız, profil oluşturma işlemi uygulamayı kapanana kadar devam eder, ardından veriler kaydedilir.|
|`-LeaveNativeImages`|Kullanılan yerel görüntülerin senaryo çalıştırıldıktan sonra kaldırılmayacağını belirtir. Bu seçenek öncelikle senaryo için belirttiğiniz uygulamayı çalıştırırken kullanılır. Mpgo.exe'nin sonraki çalışmaları için yerel görüntülerin yeniden oluşturulmasını önler. Bu seçeneği belirtirseniz, uygulamanızı çalıştırmayı tamamladığınızda, önbellekte üst öğesi olmayan yerel görüntüler olabilir. Bu durumda, Mpgo.exe'yi aynı senaryo ve derleme `–RemoveNativeImages` listesiyle çalıştırın ve bu yerel görüntüleri kaldırmak için parametreyi kullanın.|
|`-RemoveNativeImages`|Belirtilen çalışmadan `–LeaveNativeImages` temizler. `-RemoveNativeImages`Belirtirseniz, Mpgo.exe dışında `-64bit` `–AssemblyList`herhangi bir bağımsız değişkeni yoksa ve tüm enstrümanted yerel görüntüleri kaldırdıktan sonra çıkar.|

## <a name="remarks"></a>Açıklamalar
 Komut satırında `–AssemblyList` `- AssemblyListFile` hem de birden çok kez kullanabilirsiniz.

 Derlemeleri belirtirken tam yol adları belirtmezseniz, Mpgo.exe geçerli dizinde arar. Yanlış bir yol belirtirseniz, Mpgo.exe bir hata iletisi görüntüler, ancak diğer derlemeler için veri oluşturmaya devam eder. Eğitim senaryosu sırasında yüklenmemiş bir derleme belirtirseniz, o derleme için eğitim verisi oluşturulmaz.

 Listedeki bir derleme genel derleme önbelleğinde ise, profil bilgilerini içerecek şekilde güncelleştirilmez.  Profil bilgilerini toplamak için onu genel derleme önbelleğinden kaldırın.

 Ngen.exe ve Mpgo.exe'nin kullanılması yalnızca yönetilen büyük uygulamalar için önerilir, çünkü önceden derlenmiş yerel görüntülerin yararı genellikle yalnızca çalışma zamanında önemli ölçüde JIT derlemesini kaldırdığında görülür. Çalışma-yoğun ayarlanmış olmayan "Hello World" tarzı uygulamalar üzerinde Mpgo.exe çalışan herhangi bir fayda sağlamaz, ve Mpgo.exe bile profil verileri toplamak için başarısız olabilir.

> [!NOTE]
> Ngen.exe ve Mpgo.exe, ASP.NET uygulamaları ve Windows Communication Foundation (WCF) hizmetleri için önerilmez.  
  
## <a name="to-use-mpgoexe"></a>Mpgo.exe'yi kullanmak için  
  
1. Visual Studio Ultimate 2012 ve uygulamanızın yüklü olduğu bir bilgisayar kullanın.  
  
2. Mpgo.exe'yi bir yönetici olarak gerekli parametrelerle çalıştırın.  Örnek komutlar için sonraki bölüme bakın.  
  
     En iyi duruma getirilmiş ara dil (IL) derlemeleri `–OutDir` parametre tarafından belirtilen klasörde oluşturulur (örneklerde, bu `C:\Optimized` klasördür).  
  
3. Ngen.exe için kullandığınız IL derlemelerini, dizinin profil bilgilerini içeren yeni IL derlemeleriyle `–OutDir`değiştirin.  
  
4. Mpgo.exe tarafından sağlanan görüntüleri kullanan uygulama kurulumu en iyi duruma getirilmiş yerel görüntüleri yükler.  
  
## <a name="suggested-workflow"></a>Önerilen İş Akışı  
  
1. `–Scenario` Parametre ile Mpgo.exe kullanarak optimize il derlemeleri kümesi oluşturun.  
  
2. En iyi duruma getirilmiş IL derlemelerini kaynak denetime girin.  
  
3. Yapı işleminde, Ngen.exe'ye `–Import` geçmek için optimize edilmiş IL görüntüleri oluşturmak için mpgo.exe'yi bir post-build adımı olarak parametreile arayın.  
  
 Bu işlem tüm derlemelerin en iyi duruma getirilmiş verilere sahip olmasını sağlar. Güncelleştirilmiş en iyi duruma getirilmiş derlemeleri daha sık iade ederseniz (1. ve 2. adım), tüm üretim geliştirme sürecinde performans numaraları daha tutarlı olur.  
  
## <a name="using-mpgoexe-from-visual-studio"></a>Visual Studio'dan Mpgo.exe'yi kullanma  
 Visual Studio'dan Mpgo.exe'yi çalıştırabilirsiniz (bkz. makale [ye nasıl yapılır: Yapı Olaylarını Belirt (C#) )](/visualstudio/ide/how-to-specify-build-events-csharp)aşağıdaki kısıtlamalarla:  
  
- Visual Studio makroları aynı zamanda varsayılan olarak sonlarında eğik çizgiler içerdiğinden, sonda eğik çizgileri olan tırnak işaretli yollar kullanamazsınız. (Örneğin, `–OutDir "C:\Output Folder\"` geçersizdir.) Bu kısıtlamayı aşmak için, sondaki eğik çizgiden kaçabilirsiniz. (Örneğin, bunun `-OutDir "$(OutDir)\"` yerine kullanın.)  
  
- Varsayılan olarak, Mpgo.exe Visual Studio yapı yolu üzerinde değildir. Yolu Visual Studio'ya eklemeli ya da Mpgo komut satırında tam yolu belirtmelisiniz. Visual Studio'daki `–Scenario` yapı `–Import` sonrası etkinlikte parametreyi veya parametreyi kullanabilirsiniz. Ancak, tipik işlem Visual `–Scenario` Studio için Geliştirici Komut Komut Ustem'den bir kez kullanmak ve sonra her yapıdan sonra en iyi duruma getirilmiş derlemeleri güncelleştirmek için kullanmaktır; `–Import` örneğin: `"C:\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\mpgo.exe" -import "$(OutDir)tmp" -assemblylist "$(TargetPath)" -outdir "$(OutDir)\"`.  
  
<a name="samples"></a>
## <a name="examples"></a>Örnekler  
 Visual Studio için Geliştirici Komut Komut Komut Ustem aşağıdaki Mpgo.exe komutu bir vergi uygulaması optimize eder:  
  
```console  
mpgo –scenario "C:\MyApp\MyTax.exe /params par" –AssemblyList Mytax.dll MyTaxUtil2011.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 Aşağıdaki Mpgo.exe komut bir ses uygulamasını en iyi duruma getirir:  
  
```console  
mpgo –scenario "C:\MyApp\wav2wma.exe –input song1.wav –output song1.wma" –AssemblyList transcode.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 Aşağıdaki Mpgo.exe komutu yeni sürümleri en iyi duruma getirmek için daha önce en iyi duruma getirilmiş derlemelere ait verileri kullanır:  
  
```console  
mpgo.exe -import "C:\Optimized" -assemblylist "C:\MyApp\MyTax.dll" "C:\MyApp\MyTaxUtil2011.dll" -outdir C:\ReOptimized  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ngen.exe (Yerel Görüntü Oluşturucu)](ngen-exe-native-image-generator.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
- [Masaüstü Uygulamalarınız için Başlatma Performansını Artırma](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/)
- [.NET 4.5'teki Performans İyileştirmelerine Genel Bakış](https://docs.microsoft.com/archive/msdn-magazine/2012/april/clr-an-overview-of-performance-improvements-in-net-4-5)
