---
title: Mpgo.exe (Yönetilen Profil Temelli İyileştirme Aracı)
description: Yönetilen profil temelli Iyileştirme aracı Mpgo.exe kullanın. Bu araçla, yerel görüntü Oluşturucu (Ngen.exe) tarafından oluşturulan yerel görüntü derlemelerini iyileştirin.
ms.date: 03/30/2017
helpviewer_keywords:
- Mpgo.exe
- training scenarios, generating profiles with
- Managed Profile Guided Optimization Tool
- Ngen.exe
- Ngen.exe, profilers and native images
ms.assetid: f6976502-a000-4fbe-aaf5-a7aab9ce4ec2
ms.openlocfilehash: 714715968388325713a12027fb0ab89415e1d60c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544290"
---
# <a name="mpgoexe-managed-profile-guided-optimization-tool"></a>Mpgo.exe (Yönetilen Profil Temelli İyileştirme Aracı)

Yönetilen profil temelli Iyileştirme Aracı (Mpgo.exe), [Yerel Görüntü Oluşturucu (Ngen.exe)](ngen-exe-native-image-generator.md)tarafından oluşturulan yerel görüntü derlemelerini iyileştirmek için ortak Son Kullanıcı senaryolarını kullanan bir komut satırı aracıdır. Bu araç, profil verilerini oluşturan eğitim senaryolarını çalıştırmanızı sağlar. [Yerel Görüntü Oluşturucu (Ngen.exe)](ngen-exe-native-image-generator.md) , oluşturulan yerel görüntü uygulama derlemelerini iyileştirmek için bu verileri kullanır. Eğitim senaryosu, uygulamanızın beklenen bir kullanımına ilişkin denemedir. Mpgo.exe, Visual Studio Ultimate 2012 ve sonraki sürümlerinde kullanılabilir. Visual Studio 2013 başlayarak, Windows 8. x mağaza uygulamalarını iyileştirmek için Mpgo.exe de kullanabilirsiniz.  
  
Profil destekli en iyi duruma getirme süreci, eğitim senaryolarından veri toplayıp yerel görüntülerin düzenini en iyi duruma getirmek üzere onları kullanarak verimi, bellek kullanımını (çalışma kümesi boyutu) ve uygulama başlatma süresini iyileştirir.  
  
Ara Dil (IL) derlemeleri için başlatma süresi ve çalışma kümesi boyutuyla ilgili performansı sorunlarıyla karşılaştığınızda, just-in-time (JIT) (tam zamanında) derleme maliyetlerini ortadan kaldırmak ve kod paylaşımını kolaylaştırmak için ilk Ngen.exe'yi kullanmanızı öneririz. Ek geliştirmeler gerekiyorsa, uygulamanızı daha ileri düzeyde iyi hale getirmek etmek için Mpgo.exe kullanabilirsiniz. Performans artışlarını değerlendirmek için temel olarak, en iyi duruma getirilmemiş yerel görüntü derlemelerindeki performans verilerini kullanabilirsiniz. Mpgo.exe kullanıldığında soğuk başlangıç sürelerinde kısalma ve çalışma kümesi boyutunda azalma görülebilir. Mpgo.exe, en iyi duruma getirilmiş yerel görüntü derlemeleri oluşturmak için Ngen.exe'yi kullanan IL derlemelerine bilgi ekler. Daha fazla bilgi için bkz. .NET blogda [Masaüstü uygulamalarınız Için başlatma performansını iyileştirme](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/) girişi.  
  
Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, yönetici kimlik bilgileriyle Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın ve komut istemine aşağıdakini yazın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  
  
Masaüstü uygulamaları için:  
  
```console  
mpgo –Scenario <command> [-Import <directory>] –AssemblyList <assembly1>  <assembly2> ... -OutDir <directory> [options]  
```  
  
Windows 8. x Mağazası uygulamaları için:  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
mpgo –Scenario <packageName> -AppID <appId> -Timeout <seconds>  
```  
  
## <a name="parameters"></a>Parametreler  
 Mpgo.exe için tüm bağımsız değişkenler büyük/küçük harfe duyarsızdır. Komutlara önek olarak bir tire işareti eklenir.  
  
> [!NOTE]
> `–Scenario`Ya da `–Import` gerekli bir komut olarak kullanabilirsiniz, ancak ikisini birden kullanamazsınız. Seçeneğini belirtirseniz gerekli parametrelerin hiçbiri kullanılmaz `–Reset` .

|Gerekli parametre|Description|
|------------------------|-----------------|
|`-Scenario` \<*command*><br /><br /> —veya—<br /><br /> `-Scenario` \<*packageName*><br /><br /> -veya-<br /><br /> `-Import` \<*directory*>|Masaüstü uygulamaları için, `–Scenario` komut satırı bağımsız değişkenleri dahil olmak üzere iyileştirmek istediğiniz uygulamayı çalıştırmak için komutunu belirtmek üzere kullanın. Boşluklar içeren bir yol belirtiyorsa *komut* etrafında üç çift tırnak işareti kümesini kullanın; Örneğin: `mpgo.exe -scenario """C:\My App\myapp.exe""" -assemblylist """C:\My App\myapp.exe""" -outdir "C:\optimized files"` . Çift tırnak işareti kullanmayın; *komut* boşluk içeriyorsa, bunlar düzgün çalışmayacaktır.<br /><br /> -veya-<br /><br /> Windows 8. x Mağazası uygulamaları için `–Scenario` profil bilgilerini oluşturmak istediğiniz paketi belirtmek üzere kullanın. Tam paket adı yerine, paketin görünen adını veya paket aile adını belirtirseniz ve yalnızca tek bir eşleşme varsa Mpgo.exe sağladığınız adla eşleşen paketi seçer. Belirtilen adla eşleşen birden çok paket varsa, Mpgo.exe sizden bir paket seçmenizi ister.<br /><br /> —veya—<br /><br /> `-Import`' Deki derlemeleri iyileştirmek için önceden iyileştirilmiş derlemelerin en iyi duruma getirme verilerinin kullanılması gerektiğini belirtmek için kullanın `-AssemblyList` . *Dizin* , önceden iyileştirilmiş dosyaları içeren dizini belirtir. Veya içinde belirtilen derlemeler `–AssemblyList` , `–AssemblyListFile` içeri aktarılan dosyalardaki veriler kullanılarak en iyi duruma getirilecek derlemelerin yeni sürümleridir. Derlemelerin eski sürümlerine ait en iyi duruma getirme verilerini kullanmak, senaryoyu yeniden çalıştırmadan derlemelerin yeni sürümlerini en iyi duruma getirmenizi sağlar.  Ancak, içe aktarılan ve hedef derlemeler önemli ölçüde farklı kodlar içeriyorsa, en iyi duruma getirme verileri etkisiz olur. Veya içinde belirtilen derleme adları `–AssemblyList` , `–AssemblyListFile` Dizin tarafından belirtilen dizinde bulunmalıdır `–Import` *directory*. Boşluk içeren bir yol belirtiyorsa *Dizin* etrafında üç çift tırnak işareti kümesini kullanın.<br /><br /> Ya da parametresini belirtmeniz `–Scenario` gerekir `–Import` .|
|`-OutDir` \<*directory*>|En iyi duruma getirilmiş derlemelerin yerleştirileceği dizin. Çıkış dizini klasöründe bir derleme zaten varsa, yeni bir kopya oluşturulur ve adına bir dizin numarası eklenir; Örneğin: *assemblyname*-1.exe. Boşluk içeren bir yol belirtiyorsa *Dizin* etrafında çift tırnak işareti kullanın.|
|`-AssemblyList` \<*assembly1 assembly2 ...*><br /><br /> —veya—<br /><br /> `-AssemblyListFile` \<*file*>|Hakkında profil bilgileri toplamak istediğiniz derlemeleri (.exe ve .dll dosyaları gibi) boşluklarla ayrılmış olarak içeren bir liste. `C:\Dir\*.dll` `*.dll` Belirtilen veya geçerli çalışma dizinindeki tüm derlemeleri belirtebilir veya seçebilirsiniz. Daha fazla bilgi için Açıklamalar bölümüne bakın.<br /><br /> —veya—<br /><br /> Her satırda bir derleme olacak şekilde, hakkında profil bilgileri toplamak istediğiniz derlemelerin listesini içeren bir metin dosyası. Bir derleme adı tire işareti (-) ile başlıyorsa, bir derleme dosyası listesi kullanın veya derlemeyi yeniden adlandırın.|
|`-AppID` \<*appId*>|Belirtilen paketteki uygulamanın kimliği. Joker karakteri ( \* ) kullanırsanız, Mpgo.exe paketteki Appıds değerlerini numaralandırmaya çalışır ve geri dönecektir \<*package_family_name*> ! Uygulama başarısız olursa. Başında önek olarak ünlem işareti (!) konmuş bir dize belirtirseniz, Mpgo.exe paket aile adını sağlanan bağımsız değişkenle birleştirir.|
|`-Timeout` \<*seconds*>|Uygulama gelmeden önce Windows 8. x Mağazası uygulamasının çalışmasına izin verme süresi.|

|İsteğe bağlı parametre|Description|
|------------------------|-----------------|
|`-64bit`|64-bit sistemler için derlemeleri kullanır.  Derlemeniz kendisini 64-bit olarak bildiriyor olsa da 64-bit derlemeler için bu parametreyi belirtmelisiniz.|
|`-ExeConfig` \<*filename*>|Senaryonuzun sürüm ve yükleyici bilgilerini sağlamak üzere kullandığı yapılandırma dosyasını belirtir.|
|`-f`|İmzalanmış olsa da, ikili bir derlemeye profil verilerinin eklenmesini sağlar.  Derleme imzalanmışsa, yeniden imzalanması gerekir; aksi takdirde derleme yüklenemez ve çalıştırılamaz.|
|`-Reset`|İptal edilen bir profil oluşturma oturumunun derlemelerinizi etkilemediğinden emin olmak için ortamı sıfırlar ve ardından çıkış yapar. Ortam varsayılan olarak bir profil oluşturma oturumundan önce ve sonra sıfırlanır.|
|`-Timeout` \<*time in seconds*>|Profil oluşturma süresini saniye cinsinden belirtir. GUI uygulamaları için, gözlemlenen başlangıç zamanlarınızdan biraz daha büyük bir değer kullanın. Uygulama çalışmaya devam etse de, zaman aşımı süresinin sonunda profil verileri kaydedilir. Bu seçeneği ayarlamazsanız, profil oluşturma işlemi uygulamayı kapanana kadar devam eder, ardından veriler kaydedilir.|
|`-LeaveNativeImages`|Kullanılan yerel görüntülerin senaryo çalıştırıldıktan sonra kaldırılmayacağını belirtir. Bu seçenek öncelikle senaryo için belirttiğiniz uygulamayı çalıştırırken kullanılır. Mpgo.exe'nin sonraki çalışmaları için yerel görüntülerin yeniden oluşturulmasını önler. Bu seçeneği belirtirseniz, uygulamanızı çalıştırmayı tamamladığınızda, önbellekte üst öğesi olmayan yerel görüntüler olabilir. Bu durumda, aynı senaryo ve derleme listesi ile Mpgo.exe çalıştırın ve `–RemoveNativeImages` Bu yerel görüntüleri kaldırmak için parametresini kullanın.|
|`-RemoveNativeImages`|Belirtilen bir çalıştırmanın ölçeğini temizler `–LeaveNativeImages` . `-RemoveNativeImages`' I belirtirseniz, Mpgo.exe hariç tüm bağımsız değişkenleri `-64bit` yoksayar `–AssemblyList` ve tüm belgelenmiş yerel görüntüleri kaldırdıktan sonra çıkar.|

## <a name="remarks"></a>Açıklamalar
 Komut satırında hem hem `–AssemblyList` de `- AssemblyListFile` birden çok kez kullanabilirsiniz.

 Derlemeleri belirtirken tam yol adları belirtmezseniz, Mpgo.exe geçerli dizinde arar. Yanlış bir yol belirtirseniz, Mpgo.exe bir hata iletisi görüntüler, ancak diğer derlemeler için veri oluşturmaya devam eder. Eğitim senaryosu sırasında yüklenmemiş bir derleme belirtirseniz, o derleme için eğitim verisi oluşturulmaz.

 Listedeki bir derleme genel derleme önbelleğinde ise, profil bilgilerini içerecek şekilde güncelleştirilmez.  Profil bilgilerini toplamak için onu genel derleme önbelleğinden kaldırın.

 Ngen.exe ve Mpgo.exe'nin kullanılması yalnızca yönetilen büyük uygulamalar için önerilir, çünkü önceden derlenmiş yerel görüntülerin yararı genellikle yalnızca çalışma zamanında önemli ölçüde JIT derlemesini kaldırdığında görülür. Yoğun bir şekilde ayarlı olmayan "Merhaba Dünya" stil uygulamalarında Mpgo.exe çalıştırmak, daha fazla avantaj sağlamayacaktır ve Mpgo.exe profil verilerini toplayamayabilir.

> [!NOTE]
> Ngen.exe ve Mpgo.exe, ASP.NET uygulamaları ve Windows Communication Foundation (WCF) hizmetleri için önerilmez.  
  
## <a name="to-use-mpgoexe"></a>Mpgo.exe'yi kullanmak için  
  
1. Visual Studio Ultimate 2012 ve uygulamanızın yüklü olduğu bir bilgisayar kullanın.  
  
2. Mpgo.exe'yi bir yönetici olarak gerekli parametrelerle çalıştırın.  Örnek komutlar için sonraki bölüme bakın.  
  
     İyileştirilmiş ara dil (IL) derlemeleri, parametresi tarafından belirtilen klasörde oluşturulur `–OutDir` (örneklerde, bu `C:\Optimized` klasördür).  
  
3. Ngen.exe için kullandığınız Il derlemelerini, tarafından belirtilen dizinden profil bilgilerini içeren yeni Il Derlemeleriyle değiştirin `–OutDir` .  
  
4. Mpgo.exe tarafından sağlanan görüntüleri kullanan uygulama kurulumu en iyi duruma getirilmiş yerel görüntüleri yükler.  
  
## <a name="suggested-workflow"></a>Önerilen İş Akışı  
  
1. Parametresiyle Mpgo.exe kullanarak en iyileştirilmiş bir IL derlemeleri kümesi oluşturun `–Scenario` .  
  
2. En iyi duruma getirilmiş IL derlemelerini kaynak denetime girin.  
  
3. Yapı sürecinde, `–Import` Ngen.exe geçirilecek IYILEŞTIRILMIŞ Il görüntüleri oluşturmak için derleme sonrası bir adım olarak parametresiyle Mpgo.exe çağırın.  
  
 Bu işlem tüm derlemelerin en iyi duruma getirilmiş verilere sahip olmasını sağlar. Güncelleştirilmiş en iyi duruma getirilmiş derlemeleri daha sık iade ederseniz (1. ve 2. adım), tüm üretim geliştirme sürecinde performans numaraları daha tutarlı olur.  
  
## <a name="using-mpgoexe-from-visual-studio"></a>Visual Studio'dan Mpgo.exe'yi kullanma  
 Visual Studio 'dan Mpgo.exe çalıştırabilirsiniz (bkz. [nasıl yapılır: yapı olaylarını belirtme (C#)](/visualstudio/ide/how-to-specify-build-events-csharp)) aşağıdaki kısıtlamalara göre:  
  
- Visual Studio makroları aynı zamanda varsayılan olarak sonlarında eğik çizgiler içerdiğinden, sonda eğik çizgileri olan tırnak işaretli yollar kullanamazsınız. (Örneğin, `–OutDir "C:\Output Folder\"` geçersiz.) Bu kısıtlamayı geçici olarak çözmek için sondaki eğik çizgiden çıkma yapabilirsiniz. (Örneğin, `-OutDir "$(OutDir)\"` bunun yerine kullanın.)  
  
- Varsayılan olarak, Mpgo.exe Visual Studio yapı yolu üzerinde değildir. Yolu Visual Studio'ya eklemeli ya da Mpgo komut satırında tam yolu belirtmelisiniz. `–Scenario` `–Import` Visual Studio 'da derleme sonrası olayında ya da parametresini kullanabilirsiniz. Ancak, tipik işlem, `–Scenario` Visual Studio için geliştirici komut istemi bir kez kullanılır ve ardından `–Import` her derlemeden sonra iyileştirilmiş derlemeleri güncelleştirmek için kullanılır; Örneğin:  `"C:\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\mpgo.exe" -import "$(OutDir)tmp" -assemblylist "$(TargetPath)" -outdir "$(OutDir)\"` .  
  
<a name="samples"></a>
## <a name="examples"></a>Örnekler  
 Visual Studio için bir Geliştirici Komut İstemi aşağıdaki Mpgo.exe komutu bir vergi uygulamasını iyileştirir:  
  
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

- [Ngen.exe (yerel görüntü Oluşturucu)](ngen-exe-native-image-generator.md)
- [Komut Istemleri](developer-command-prompt-for-vs.md)
- [Masaüstü uygulamalarınız için başlatma performansını artırma](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/)
- [.NET 4,5 performans Iyileştirmelerine genel bakış](/archive/msdn-magazine/2012/april/clr-an-overview-of-performance-improvements-in-net-4-5)
