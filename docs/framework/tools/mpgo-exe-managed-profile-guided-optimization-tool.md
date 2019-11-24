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
ms.openlocfilehash: a5ab3040a246a135771c45b2639567db9ab510e3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447964"
---
# <a name="mpgoexe-managed-profile-guided-optimization-tool"></a>Mpgo.exe (Yönetilen Profil Temelli İyileştirme Aracı)

The Managed Profile Guided Optimization Tool (Mpgo.exe) is a command-line tool that uses common end-user scenarios to optimize the native image assemblies that are created by the [Native Image Generator (Ngen.exe)](ngen-exe-native-image-generator.md). Bu araç, profil verilerini oluşturan eğitim senaryolarını çalıştırmanızı sağlar. The [Native Image Generator (Ngen.exe)](ngen-exe-native-image-generator.md) uses this data to optimize its generated native image application assemblies. Eğitim senaryosu, uygulamanızın beklenen bir kullanımına ilişkin denemedir. Mpgo.exe, Visual Studio Ultimate 2012 ve sonraki sürümlerinde kullanılabilir. Starting with Visual Studio 2013, you can also use Mpgo.exe to optimize Windows 8.x Store apps.  
  
Profil destekli en iyi duruma getirme süreci, eğitim senaryolarından veri toplayıp yerel görüntülerin düzenini en iyi duruma getirmek üzere onları kullanarak verimi, bellek kullanımını (çalışma kümesi boyutu) ve uygulama başlatma süresini iyileştirir.  
  
Ara Dil (IL) derlemeleri için başlatma süresi ve çalışma kümesi boyutuyla ilgili performansı sorunlarıyla karşılaştığınızda, just-in-time (JIT) (tam zamanında) derleme maliyetlerini ortadan kaldırmak ve kod paylaşımını kolaylaştırmak için ilk Ngen.exe'yi kullanmanızı öneririz. Ek geliştirmeler gerekiyorsa, uygulamanızı daha ileri düzeyde iyi hale getirmek etmek için Mpgo.exe kullanabilirsiniz. Performans artışlarını değerlendirmek için temel olarak, en iyi duruma getirilmemiş yerel görüntü derlemelerindeki performans verilerini kullanabilirsiniz. Mpgo.exe kullanıldığında soğuk başlangıç sürelerinde kısalma ve çalışma kümesi boyutunda azalma görülebilir. Mpgo.exe, en iyi duruma getirilmiş yerel görüntü derlemeleri oluşturmak için Ngen.exe'yi kullanan IL derlemelerine bilgi ekler. For more information, see the entry [Improving Launch Performance for your Desktop Applications](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/) in the .NET blog.  
  
Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7) with administrator credentials, and type the following at the command prompt. For more information, see [Command Prompts](developer-command-prompt-for-vs.md).  
  
Masaüstü uygulamaları için:  
  
```console  
mpgo –Scenario <command> [-Import <directory>] –AssemblyList <assembly1>  <assembly2> ... -OutDir <directory> [options]  
```  
  
For Windows 8.x Store apps:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
mpgo –Scenario <packageName> -AppID <appId> -Timeout <seconds>  
```  
  
## <a name="parameters"></a>Parametreler  
 Mpgo.exe için tüm bağımsız değişkenler büyük/küçük harfe duyarsızdır. Komutlara önek olarak bir tire işareti eklenir.  
  
> [!NOTE]
> You can use either `–Scenario` or `–Import` as a required command, but not both. None of the required parameters are used if you specify the `–Reset` option.

|Gerekli parametre|Açıklama|
|------------------------|-----------------|
|`-Scenario` \<*command*><br /><br /> —veya—<br /><br /> `-Scenario` \<*packageName*><br /><br /> veya<br /><br /> `-Import` \<*directory*>|For desktop apps, use `–Scenario` to specify the command to run the application you want to optimize, including any command-line arguments. Use three sets of double quotation marks around *command* if it specifies a path that includes spaces; for example: `mpgo.exe -scenario """C:\My App\myapp.exe""" -assemblylist """C:\My App\myapp.exe""" -outdir "C:\optimized files"`. Do not use double quotation marks; they will not work correctly if *command* includes spaces.<br /><br /> veya<br /><br /> For Windows 8.x Store apps, use `–Scenario` to specify the package that you want to generate profile information for. Tam paket adı yerine, paketin görünen adını veya paket aile adını belirtirseniz ve yalnızca tek bir eşleşme varsa Mpgo.exe sağladığınız adla eşleşen paketi seçer. Belirtilen adla eşleşen birden çok paket varsa, Mpgo.exe sizden bir paket seçmenizi ister.<br /><br /> —veya—<br /><br /> Use `-Import` to specify that optimization data from previously optimized assemblies should be used to optimize the assemblies in `-AssemblyList`. *directory* specifies the directory that contains the previously optimized files. The assemblies specified in `–AssemblyList` or `–AssemblyListFile` are the new versions of the assemblies to be optimized using the data from the imported files. Derlemelerin eski sürümlerine ait en iyi duruma getirme verilerini kullanmak, senaryoyu yeniden çalıştırmadan derlemelerin yeni sürümlerini en iyi duruma getirmenizi sağlar.  Ancak, içe aktarılan ve hedef derlemeler önemli ölçüde farklı kodlar içeriyorsa, en iyi duruma getirme verileri etkisiz olur. The assembly names specified in `–AssemblyList` or `–AssemblyListFile` must be present in the directory specified by `–Import`*directory*. Use three sets of double quotation marks around *directory* if it specifies a path that includes spaces.<br /><br /> You must specify either `–Scenario` or `–Import`, but not both parameters.|
|`-OutDir` \<*directory*>|En iyi duruma getirilmiş derlemelerin yerleştirileceği dizin. If an assembly already exists in the output directory folder, a new copy is created and an index number is appended to its name; for example: *assemblyname*-1.exe. Use double quotation marks around *directory* if it specifies a path that contains spaces.|
|`-AssemblyList` \<*assembly1 assembly2 ...* ><br /><br /> —veya—<br /><br /> `-AssemblyListFile` \<*file*>|Hakkında profil bilgileri toplamak istediğiniz derlemeleri (.exe ve .dll dosyaları gibi) boşluklarla ayrılmış olarak içeren bir liste. You can specify `C:\Dir\*.dll` or `*.dll` to select all the assemblies in the designated or current working directory. Daha fazla bilgi için Açıklamalar bölümüne bakın.<br /><br /> —veya—<br /><br /> Her satırda bir derleme olacak şekilde, hakkında profil bilgileri toplamak istediğiniz derlemelerin listesini içeren bir metin dosyası. Bir derleme adı tire işareti (-) ile başlıyorsa, bir derleme dosyası listesi kullanın veya derlemeyi yeniden adlandırın.|
|`-AppID` \<*appId*>|Belirtilen paketteki uygulamanın kimliği. If you use the wildcard (\*), Mpgo.exe will try to enumerate the AppIDs in the package and will fall back to \<*package_family_name*>!App if it fails. Başında önek olarak ünlem işareti (!) konmuş bir dize belirtirseniz, Mpgo.exe paket aile adını sağlanan bağımsız değişkenle birleştirir.|
|`-Timeout` \<*seconds*>|The amount of time to allow the Windows 8.x Store app to run before the app exits.|

|İsteğe bağlı parametre|Açıklama|
|------------------------|-----------------|
|`-64bit`|64-bit sistemler için derlemeleri kullanır.  Derlemeniz kendisini 64-bit olarak bildiriyor olsa da 64-bit derlemeler için bu parametreyi belirtmelisiniz.|
|`-ExeConfig` \<*filename*>|Senaryonuzun sürüm ve yükleyici bilgilerini sağlamak üzere kullandığı yapılandırma dosyasını belirtir.|
|`-f`|İmzalanmış olsa da, ikili bir derlemeye profil verilerinin eklenmesini sağlar.  Derleme imzalanmışsa, yeniden imzalanması gerekir; aksi takdirde derleme yüklenemez ve çalıştırılamaz.|
|`-Reset`|İptal edilen bir profil oluşturma oturumunun derlemelerinizi etkilemediğinden emin olmak için ortamı sıfırlar ve ardından çıkış yapar. Ortam varsayılan olarak bir profil oluşturma oturumundan önce ve sonra sıfırlanır.|
|`-Timeout` \<*time in seconds*>|Profil oluşturma süresini saniye cinsinden belirtir. GUI uygulamaları için, gözlemlenen başlangıç zamanlarınızdan biraz daha büyük bir değer kullanın. Uygulama çalışmaya devam etse de, zaman aşımı süresinin sonunda profil verileri kaydedilir. Bu seçeneği ayarlamazsanız, profil oluşturma işlemi uygulamayı kapanana kadar devam eder, ardından veriler kaydedilir.|
|`-LeaveNativeImages`|Kullanılan yerel görüntülerin senaryo çalıştırıldıktan sonra kaldırılmayacağını belirtir. Bu seçenek öncelikle senaryo için belirttiğiniz uygulamayı çalıştırırken kullanılır. Mpgo.exe'nin sonraki çalışmaları için yerel görüntülerin yeniden oluşturulmasını önler. Bu seçeneği belirtirseniz, uygulamanızı çalıştırmayı tamamladığınızda, önbellekte üst öğesi olmayan yerel görüntüler olabilir. In this case, run Mpgo.exe with the same scenario and assembly list and use the `–RemoveNativeImages` parameter to remove these native images.|
|`-RemoveNativeImages`|Cleans up from a run where `–LeaveNativeImages` was specified. If you specify `-RemoveNativeImages`, Mpgo.exe ignores any arguments except `-64bit` and `–AssemblyList`, and exits after removing all instrumented native images.|

## <a name="remarks"></a>Açıklamalar
 You can use both `–AssemblyList` and `- AssemblyListFile` multiple times on the command line.

 Derlemeleri belirtirken tam yol adları belirtmezseniz, Mpgo.exe geçerli dizinde arar. Yanlış bir yol belirtirseniz, Mpgo.exe bir hata iletisi görüntüler, ancak diğer derlemeler için veri oluşturmaya devam eder. Eğitim senaryosu sırasında yüklenmemiş bir derleme belirtirseniz, o derleme için eğitim verisi oluşturulmaz.

 Listedeki bir derleme genel derleme önbelleğinde ise, profil bilgilerini içerecek şekilde güncelleştirilmez.  Profil bilgilerini toplamak için onu genel derleme önbelleğinden kaldırın.

 Ngen.exe ve Mpgo.exe'nin kullanılması yalnızca yönetilen büyük uygulamalar için önerilir, çünkü önceden derlenmiş yerel görüntülerin yararı genellikle yalnızca çalışma zamanında önemli ölçüde JIT derlemesini kaldırdığında görülür. Running Mpgo.exe on "Hello World" style applications that aren’t working-set intensive will not provide any benefits, and Mpgo.exe may even fail to gather profile data.

> [!NOTE]
> Ngen.exe ve Mpgo.exe, ASP.NET uygulamaları ve Windows Communication Foundation (WCF) hizmetleri için önerilmez.  
  
## <a name="to-use-mpgoexe"></a>Mpgo.exe'yi kullanmak için  
  
1. Visual Studio Ultimate 2012 ve uygulamanızın yüklü olduğu bir bilgisayar kullanın.  
  
2. Mpgo.exe'yi bir yönetici olarak gerekli parametrelerle çalıştırın.  Örnek komutlar için sonraki bölüme bakın.  
  
     The optimized intermediate language (IL) assemblies are created in the folder specified by the `–OutDir` parameter (in the examples, this is the `C:\Optimized` folder).  
  
3. Replace the IL assemblies you used for Ngen.exe  with the new IL assemblies that contain the profile information from the directory specified by `–OutDir`.  
  
4. Mpgo.exe tarafından sağlanan görüntüleri kullanan uygulama kurulumu en iyi duruma getirilmiş yerel görüntüleri yükler.  
  
## <a name="suggested-workflow"></a>Önerilen İş Akışı  
  
1. Create a set of optimized IL assemblies by using Mpgo.exe with the `–Scenario` parameter.  
  
2. En iyi duruma getirilmiş IL derlemelerini kaynak denetime girin.  
  
3. In the build process, call Mpgo.exe with the `–Import` parameter as a post-build step to generate optimized IL images to pass to Ngen.exe.  
  
 Bu işlem tüm derlemelerin en iyi duruma getirilmiş verilere sahip olmasını sağlar. Güncelleştirilmiş en iyi duruma getirilmiş derlemeleri daha sık iade ederseniz (1. ve 2. adım), tüm üretim geliştirme sürecinde performans numaraları daha tutarlı olur.  
  
## <a name="using-mpgoexe-from-visual-studio"></a>Visual Studio'dan Mpgo.exe'yi kullanma  
 You can run Mpgo.exe from Visual Studio (see the article [How to: Specify Build Events (C#)](/visualstudio/ide/how-to-specify-build-events-csharp)) with the following restrictions:  
  
- Visual Studio makroları aynı zamanda varsayılan olarak sonlarında eğik çizgiler içerdiğinden, sonda eğik çizgileri olan tırnak işaretli yollar kullanamazsınız. (For example, `–OutDir "C:\Output Folder\"` is invalid.) To work around this restriction, you can escape the trailing slash. (For example, use `-OutDir "$(OutDir)\"` instead.)  
  
- Varsayılan olarak, Mpgo.exe Visual Studio yapı yolu üzerinde değildir. Yolu Visual Studio'ya eklemeli ya da Mpgo komut satırında tam yolu belirtmelisiniz. You can use either the `–Scenario` or the `–Import` parameter in the post-build event in Visual Studio. However, the typical process is to use `–Scenario` one time from a Developer Command Prompt for Visual Studio, and then use `–Import` to update the optimized assemblies after each build; for example:  `"C:\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\mpgo.exe" -import "$(OutDir)tmp" -assemblylist "$(TargetPath)" -outdir "$(OutDir)\"`.  
  
<a name="samples"></a>   
## <a name="examples"></a>Örnekler  
 The following Mpgo.exe command from a Developer Command Prompt for Visual Studio optimizes a tax application:  
  
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
- [Improving Launch Performance for your Desktop Applications](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/)
- [An Overview of Performance Improvements in .NET 4.5](https://docs.microsoft.com/archive/msdn-magazine/2012/april/clr-an-overview-of-performance-improvements-in-net-4-5)
