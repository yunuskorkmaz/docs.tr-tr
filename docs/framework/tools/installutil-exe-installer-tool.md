---
title: "Installutil.exe (Yükleme Aracı)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- uninstalling server resources
- removing server resources
- status information for installation
- installation progress reports
- installing server resources
- Installer tool
- Installutil.exe
- files, Installer tool
- progress information for installation
- reporting installation progress
ms.assetid: 3f9d0533-f895-4897-b4ea-528284e0241d
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 68bb098cf34839e0587864092d1af302d70eca89
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="installutilexe-installer-tool"></a>Installutil.exe (Yükleme Aracı)
Yükleyici aracı, yükleyici bileşenlerini belirli derlemelerde yürüterek sunucu kaynaklarını yüklemenize ve kaldırmanıza olanak tanıyan bir komut satırı aracıdır. Bu araç, sınıflar ile birlikte çalışır. <xref:System.Configuration.Install> ad alanı.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`assembly`|Yükleyici bileşenlerinin yürütüleceği derlemenin dosya adı. Derleme tanımlayıcı adı kullanarak belirtmek istiyorsanız bu parametreyi atlayın `/AssemblyName` seçeneği.|  
  
<a name="options"></a>   
## <a name="options"></a>Seçenekler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/h[elp]`<br /><br /> veya<br /><br /> `/?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|`/help`*derleme*<br /><br /> veya<br /><br /> `/?`*derleme*|InstallUtil.exe'ye ilişkin komut sözdizimi ve seçeneklerin yanı sıra, belirtilen derleme içinde tek tek yükleyiciler tarafından tanınan ek seçenekleri görüntüler. Bu seçenek her yükleyici bileşenin tarafından döndürülen metni ekler <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> InstallUtil.exe Yardım metni özelliğine.|  
|`/AssemblyName` "*assemblyName*<br /><br /> ,Version=*major.minor.build.revision*<br /><br /> , Kültür =*yerel ayar*<br /><br /> ,PublicKeyToken=*publicKeyToken*"|Bir derlemenin, genel derleme önbelleğine kaydedilmesi gereken tanımlayıcı adını belirtir. Derleme adı, derlemenin sürüm, kültür ve genel anahtar belirteciyle birlikte belirtilmelidir. Tam olarak belirtilen ad, tırnak işareti içine alınmalıdır.<br /><br /> Örneğin, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" tam olaralk belirtilmiş bir derleme adıdır.|  
|`/InstallStateDir=[`*directoryName*`]`|Derlemeyi yüklemek için kullanılan verileri içeren .InstallState dosyasının dizinini içerir. Varsayılan değer, derlemeyi içeren dizindir.|  
|`/LogFile=`[*filename*]|Yükleme ilerlemesinin kaydedildiği günlük dosyasının adını belirtir. Varsayılan olarak, varsa `/LogFile` seçeneği atlanırsa, adlı bir günlük dosyası *assemblyname*. InstallLog oluşturulur. Varsa *filename* olan atlanırsa, herhangi bir günlük dosyası oluşturulur.|  
|`/LogToConsole`={`true`&#124;`false`}|Varsa `true`, konsola çıktı görüntüler. Varsa `false` (varsayılan), konsola çıktı gizler.|  
|`/ShowCallStack`|Yükleme sırasında herhangi bir noktada bir özel durum oluşursa, çağrı yığınını günlük dosyana çıkış olarak aktarır.|  
|`/u`[`ninstall`]|Belirtilen derlemeleri kaldırır. Diğer Seçenekler aksine `/u` seçeneği komut satırında göründüğü bağımsız olarak tüm derlemeler için geçerlidir.|  
  
<a name="cmdline"></a>   
## <a name="additional-installer-options"></a>Ek Yükleyici Seçenekleri  
 Bir derlemede kullanılan bağımsız yükleyiciler seçenekleri de listelenenlere tanıması [seçenekleri](#options) bölümü. Bu seçenekler hakkında bilgi edinmek için komut satırında ile birlikte derlemeler yollar ile InstallUtil.exe çalıştırmak `/?` veya `/help` seçeneği. Bu seçenekleri belirtmek için, bunları, InstallUtil.exe tarafından tanınan seçeneklerin yanı sıra komut satırına ekleyebilirsiniz.  
  
> [!NOTE]
>  Tek tek yükleyici bileşenler tarafından desteklenen seçenekler hakkında Yardım metni tarafından döndürülen <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliği. Komut satırında girilen tek seçenekler erişilebilir program aracılığıyla <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> özelliği.  
  
 Tüm seçenekler ve komut satırı parametreleri yükleme günlük dosyasına yazılır. Ancak, kullanırsanız `/Password` bazı yükleyici bileşenleri tarafından tanınan, parametre parola bilgilerini tarafından sekiz yıldız işareti (*) değiştirilecek ve günlük dosyasında görünmez.  
  
> [!IMPORTANT]
>  Bazı durumlarda, yükleyiciye geçirilen ve varsayılan olarak düz bir metin günlüğü dosyasına yazılan, hassas veya kişisel olarak tanımlanabilir bilgiler içerebilir. Bu davranışı önlemek için günlük dosyası belirterek gizleyebilirsiniz `/LogFile=` (hiçbir *filename* bağımsız değişkeni) komut satırında Installutil.exe sonra.  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework uygulamaları, uygulama dağıtıldığında oluşturulması gereken ileti kuyrukları, olay günlükleri ve performans sayaçları gibi geleneksel program dosyalarından ve ilişkili kaynaklardan oluşur. Uygulamanız yüklendiğinde bu kaynakları oluşturmak ve uygulamanız kaldırıldığında kaldırmak için, bir derlemenin yükleyici bileşenlerini kullanabilirsiniz. Installutil.exe, bu yükleyici bileşenlerini algılar ve çalıştırır.  
  
 Aynı komut satırında birden çok derleme belirtebilirsiniz. Derleme adından önce gelen herhangi bir seçenek o derlemenin yüklemesine uygulanır. Dışında `/u` ve `/AssemblyName`, seçenekleri toplu ancak geçersiz kılınabilir. Diğer bir deyişle, bir derleme için belirtilen seçenekler, seçenek yeni bir değerle belirtilmediği sürece sonraki tüm derlemelere uygulanır.  
  
 Installutil.exe'yi herhangi bir seçenek belirtmeden bir derlemeye yönelik olarak çalıştırırsanız, aşağıdaki üç dosyayı derlemenin dizinine yerleştirir:  
  
-   InstallUtil.InstallLog - Yükleme ilerlemesinin genel bir açıklamasını içerir.  
  
-   *AssemblyName*. InstallLog - yükleme işlemi yürütme aşamasında özgü bilgileri içerir. Yürütme aşaması hakkında daha fazla bilgi için bkz: <xref:System.Configuration.Install.Installer.Commit%2A> yöntemi.  
  
-   *AssemblyName*. InstallState - derlemesini kaldırmak için kullanılan verileri içerir.  
  
 Belirtilen derlemelere incelenecek ve tüm bulmak için Installutil.exe kullanır yansıma <xref:System.Configuration.Install.Installer> türleri <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> özniteliği kümesine `true`. Araç ardından ya da yürütür <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> veya <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> yöntemi her örneği üzerinde <xref:System.Configuration.Install.Installer> türü. Installutil.exe, yüklemeyi işlemsel bir şekilde gerçekleştirir; yani, derlemelerden birisi yüklenemezse, diğer tüm derlemelerin yüklemelerini geri alır. Kaldırma, işlemsel değildir.  
  
 Installutil.exe, gecikme imzalı derlemeleri yükleyemez veya kaldıramaz, fakat tanımlayıcı adlı derlemeleri yükleyebilir veya kaldırabilir.  
  
 .NET Framework sürüm 2.0 ile başlayarak, ortak dil çalışma zamanının (CLR) 32 bit sürümü Yükleyici aracının yalnızca 32 bit sürümüyle birlikte sevk edilir, fakat CLR'nin 64 bit sürümü Yükleyici aracının hem 32 bit hem de 64 bit sürümleriyle birlikte sevk edilir. 64 bit CLR kullanırken, 32 bit derlemeleri yüklemek için 32 bit Yükleyici aracını, 64 bit ve Microsoft ara dil (MSIL) derlemelerini yüklemek içinse 64 bit Yükleyici aracını kullanın. Yükleyici aracının her iki sürümü de aynı şekilde davranır.  
  
 Installutil.exe C++ derleyicisi tarafından üretilen gömülü doğal kodu tanıyamayacağından, C++ kullanarak oluşturulan bir Windows hizmetini dağıtmak için Installutil.exe'yi kullanamazsınız. C++ Windows hizmeti Installutil.exe, bir özel durum ile gibi dağıtmaya çalışırsanız <xref:System.BadImageFormatException> oluşturulur. Bu senaryoyla çalışmak için, hizmet kodunu bir C++ modülüne taşıyın ve sonra yükleyici nesnesini C# veya Visual Basic'te yazın.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, komut sözdiziminin bir açıklamasını ve InstallUtil.exe'ye ilişkin seçenekleri görüntüler.  
  
```  
installutil /?  
```  
  
 Aşağıdaki komut, komut sözdiziminin bir açıklamasını ve InstallUtil.exe'ye ilişkin seçenekleri görüntüler. Yükleyici bileşenler tarafından desteklenen seçenekler listesinde ve açıklama ayrıca görüntüler `myAssembly.exe` Yardım metni yükleyicinin atanmışsa <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliği.  
  
```  
installutil /? myAssembly.exe  
```  
  
 Aşağıdaki komutu yükleyici bileşenleri derlemede yürütür `myAssembly.exe`.  
  
```  
installutil myAssembly.exe  
```  
  
 Aşağıdaki komutu kullanarak yükleyici bileşenleri bir derlemede yürütür `/AssemblyName` anahtarı ve bir tam ad.  
  
```  
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"  
```  
  
 Aşağıdaki komut, dosya adıyla belirtilen bir derlemede ve tanımlayıcı adla belirtilen bir derlemede yükleyici bileşenlerini yürütür. Dosya adıyla belirtilen tüm derlemelerde olduğundan komut satırında güçlü adıyla belirtilen derlemeleri gelmelidir Not `/AssemblyName` seçeneği geçersiz kılınamaz.  
  
```  
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"  
```  
  
 Aşağıdaki komutu kaldırıcı bileşenleri derlemede yürütür `myAssembly.exe`.  
  
```  
installutil /u myAssembly.exe   
```  
  
 Aşağıdaki komutu uninistaller bileşenleri derlemelerde yürütür `myAssembly1.exe` ve `myAssembly2.exe`.  
  
```  
installutil myAssembly1.exe /u myAssembly2.exe  
```  
  
 Çünkü konumunu `/u` komut satırı seçeneği önemli değildir, bu aşağıdaki komutu ile eşdeğerdir.  
  
```  
installutil /u myAssembly1.exe myAssembly2.exe  
```  
  
 Aşağıdaki komutu yükleyicileri derlemede yürütür `myAssembly.exe` ve ilerleme durumu bilgileri yazılacağı belirtir `myLog.InstallLog`.  
  
```  
installutil /LogFile=myLog.InstallLog myAssembly.exe   
```  
  
 Aşağıdaki komutu yükleyicileri derlemede yürütür `myAssembly.exe`, ilerleme durumu bilgileri için yazılması gerektiğini belirtir `myLog.InstallLog`ve yükleyicilerini özel kullanır `/reg` güncelleştirmeleri sisteme yapılması gerektiğini belirtmek için seçeneği kayıt defteri.  
  
```  
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe  
```  
  
 Aşağıdaki komutu yükleyicileri derlemede yürütür `myAssembly.exe`, kullandığı yükleyici özel `/email` kullanıcının e-posta adresini belirtmek için seçenek ve çıktı günlük dosyasına gizler.  
  
```  
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe  
```  
  
 Yükleme ilerleme durumu için aşağıdaki komutu Yazar `myAssembly.exe` için `myLog.InstallLog` ve ilerleyişini Yazar `myTestAssembly.exe` için `myTestLog.InstallLog`.  
  
```  
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Configuration.Install>  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
