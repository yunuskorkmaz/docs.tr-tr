---
title: Installutil.exe (Yükleme Aracı)
ms.date: 03/30/2017
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
ms.openlocfilehash: caca946617c681ce6516b7184a9ea506cc67158d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73105068"
---
# <a name="installutilexe-installer-tool"></a>Installutil.exe (Yükleme Aracı)

Yükleyici aracı, yükleyici bileşenlerini belirli derlemelerde yürüterek sunucu kaynaklarını yüklemenize ve kaldırmanıza olanak tanıyan bir komut satırı aracıdır. Bu araç <xref:System.Configuration.Install> ad alanındaki sınıflarla birlikte çalışır.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

## <a name="parameters"></a>Parametreler

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`assembly`|Yükleyici bileşenlerinin yürütüleceği derlemenin dosya adı. Seçeneği kullanarak derlemenin güçlü adını belirtmek istiyorsanız bu parametreyi `/AssemblyName` atla.|

<a name="options"></a>

## <a name="options"></a>Seçenekler

|Seçenek|Açıklama|
|------------|-----------------|
|`/h[elp]`<br /><br /> -veya-<br /><br /> `/?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|
|`/help`*montaj*<br /><br /> -veya-<br /><br /> `/?`*montaj*|InstallUtil.exe'ye ilişkin komut sözdizimi ve seçeneklerin yanı sıra, belirtilen derleme içinde tek tek yükleyiciler tarafından tanınan ek seçenekleri görüntüler. Bu seçenek, her yükleyici bileşeninin <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliği tarafından döndürülen metni InstallUtil.exe yardım metnine ekler.|
|`/AssemblyName`"*assemblyName*<br /><br /> ,Sürüm=*major.minor.build.revision*<br /><br /> ,Kültür=*yerel*<br /><br /> ,PublicKeyToken=*publicKeyToken*"|Bir derlemenin, genel derleme önbelleğine kaydedilmesi gereken tanımlayıcı adını belirtir. Derleme adı, derlemenin sürüm, kültür ve genel anahtar belirteciyle birlikte belirtilmelidir. Tam olarak belirtilen ad, tırnak işareti içine alınmalıdır.<br /><br /> Örneğin, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" tam olaralk belirtilmiş bir derleme adıdır.|
|`/InstallStateDir=[`*directoryName*`]`|Derlemeyi yüklemek için kullanılan verileri içeren .InstallState dosyasının dizinini içerir. Varsayılan değer, derlemeyi içeren dizindir.|
|`/LogFile=`[*dosya adı*]|Yükleme ilerlemesinin kaydedildiği günlük dosyasının adını belirtir. Varsayılan olarak, `/LogFile` seçenek atlanırsa, *assemblyname*adlı bir günlük dosyası . InstallLog oluşturulur. *Dosya adı* atlanırsa, günlük dosyası oluşturulmadı.|
|`/LogToConsole`={`true` `false`&#124;}|Eğer, `true`konsola çıkış görüntüler. (varsayılan), `false` konsola çıktı bastırır.|
|`/ShowCallStack`|Yükleme sırasında herhangi bir noktada bir özel durum oluşursa, çağrı yığınını günlük dosyana çıkış olarak aktarır.|
|`/u`[`ninstall`]|Belirtilen derlemeleri kaldırır. Diğer seçeneklerin `/u` aksine, seçeneğin komut satırında nerede göründüğüne bakılmaksızın tüm derlemeler için geçerlidir.|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a>Ek Yükleyici Seçenekleri

Bir derleme içinde kullanılan tek tek yükleyiciler, [Seçenekler](#options) bölümünde listelenenseçeneklere ek olarak seçenekleri tanıyabilir. Bu seçenekler hakkında bilgi edinmek için InstallUtil.exe'yi komut satırındaki derlemelerin `/help` yollarıyla birlikte veya seçeneğiyle birlikte çalıştırın. `/?` Bu seçenekleri belirtmek için, bunları, InstallUtil.exe tarafından tanınan seçeneklerin yanı sıra komut satırına ekleyebilirsiniz.

> [!NOTE]
> Tek tek yükleyici bileşenleri tarafından desteklenen seçeneklerdeki <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> yardım metni özellik tarafından döndürülür. Komut satırına girilen tek tek seçeneklere <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> özellikten programlı olarak erişilebilir.

Tüm seçenekler ve komut satırı parametreleri yükleme günlük dosyasına yazılır. Ancak, bazı yükleyici bileşenleri tarafından tanınan `/Password` parametreyi kullanırsanız, parola bilgileri sekiz yıldız (*) ile değiştirilir ve günlük dosyasında görünmez.

> [!IMPORTANT]
> Bazı durumlarda, yükleyiciye geçirilen ve varsayılan olarak düz bir metin günlüğü dosyasına yazılan, hassas veya kişisel olarak tanımlanabilir bilgiler içerebilir. Bu davranışı önlemek için, komut satırında `/LogFile=` Installutil.exe'den sonra *(dosya adı* bağımsız değişkeni olmadan) belirterek günlük dosyasını bastırabilirsiniz.

## <a name="remarks"></a>Açıklamalar

.NET Framework uygulamaları, uygulama dağıtıldığında oluşturulması gereken ileti kuyrukları, olay günlükleri ve performans sayaçları gibi geleneksel program dosyalarından ve ilişkili kaynaklardan oluşur. Uygulamanız yüklendiğinde bu kaynakları oluşturmak ve uygulamanız kaldırıldığında kaldırmak için, bir derlemenin yükleyici bileşenlerini kullanabilirsiniz. Installutil.exe, bu yükleyici bileşenlerini algılar ve çalıştırır.

Aynı komut satırında birden çok derleme belirtebilirsiniz. Derleme adından önce gelen herhangi bir seçenek o derlemenin yüklemesine uygulanır. Dışında `/u` ve `/AssemblyName`, seçenekler kümülatif ama geçersiz. Diğer bir deyişle, bir derleme için belirtilen seçenekler, seçenek yeni bir değerle belirtilmediği sürece sonraki tüm derlemelere uygulanır.

Installutil.exe'yi herhangi bir seçenek belirtmeden bir derlemeye yönelik olarak çalıştırırsanız, aşağıdaki üç dosyayı derlemenin dizinine yerleştirir:

- InstallUtil.InstallLog - Yükleme ilerlemesinin genel bir açıklamasını içerir.

- *assemblyname*. InstallLog - Yükleme işleminin işleme aşamasına özgü bilgileri içerir. Commit aşaması hakkında daha fazla <xref:System.Configuration.Install.Installer.Commit%2A> bilgi için yönteme bakın.

- *assemblyname*. InstallState - Derlemeyi kaldırmak için kullanılan verileri içerir.

Installutil.exe, belirtilen derlemeleri incelemek ve öznitelik olarak ayarlanmış tüm <xref:System.Configuration.Install.Installer> türleri <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> bulmak için `true`yansımayı kullanır. Araç daha sonra <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> <xref:System.Configuration.Install.Installer> türün her örneğinde ya da yöntemi yürütür. Installutil.exe, yüklemeyi işlemsel bir şekilde gerçekleştirir; yani, derlemelerden birisi yüklenemezse, diğer tüm derlemelerin yüklemelerini geri alır. Kaldırma, işlemsel değildir.

Installutil.exe, gecikme imzalı derlemeleri yükleyemez veya kaldıramaz, fakat tanımlayıcı adlı derlemeleri yükleyebilir veya kaldırabilir.

.NET Framework sürüm 2.0 ile başlayarak, ortak dil çalışma zamanının (CLR) 32 bit sürümü Yükleyici aracının yalnızca 32 bit sürümüyle birlikte sevk edilir, fakat CLR'nin 64 bit sürümü Yükleyici aracının hem 32 bit hem de 64 bit sürümleriyle birlikte sevk edilir. 64 bit CLR kullanırken, 32 bit derlemeleri yüklemek için 32 bit Yükleyici aracını, 64 bit ve Microsoft ara dil (MSIL) derlemelerini yüklemek içinse 64 bit Yükleyici aracını kullanın. Yükleyici aracının her iki sürümü de aynı şekilde davranır.

Installutil.exe C++ derleyicisi tarafından üretilen gömülü doğal kodu tanıyamayacağından, C++ kullanarak oluşturulan bir Windows hizmetini dağıtmak için Installutil.exe'yi kullanamazsınız. Installutil.exe ile bir C++ Windows hizmeti dağıtmaya çalışırsanız, bunun gibi <xref:System.BadImageFormatException> bir özel durum atılır. Bu senaryoyla çalışmak için, hizmet kodunu bir C++ modülüne taşıyın ve sonra yükleyici nesnesini C# veya Visual Basic'te yazın.

## <a name="examples"></a>Örnekler

Aşağıdaki komut, komut sözdiziminin bir açıklamasını ve InstallUtil.exe'ye ilişkin seçenekleri görüntüler.

```console
installutil /?
```

Aşağıdaki komut, komut sözdiziminin bir açıklamasını ve InstallUtil.exe'ye ilişkin seçenekleri görüntüler. Ayrıca, yükleyicinin `myAssembly.exe` <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliğine yardım metni atanmışsa, yükleyici bileşenleri tarafından desteklenen seçeneklerin açıklamasını ve listesini de görüntüler.

```console
installutil /? myAssembly.exe
```

Aşağıdaki komut montajcı bileşenlerini derlemede `myAssembly.exe`yürütür.

```console
installutil myAssembly.exe
```

Aşağıdaki komut, `/AssemblyName` anahtar ve tam nitelikli bir ad kullanarak bir montaj da yükleyici bileşenleri yürütür.

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Aşağıdaki komut, dosya adıyla belirtilen bir derlemede ve tanımlayıcı adla belirtilen bir derlemede yükleyici bileşenlerini yürütür. `/AssemblyName` Seçenek geçersiz kılınamayacağından, dosya adı ile belirtilen tüm derlemelerin komut satırında güçlü adla belirtilen derlemelerden önce olması gerektiğini unutmayın.

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Aşağıdaki komut, montajdaki kaldırıcı bileşenlerini `myAssembly.exe`yürütür.

```console
installutil /u myAssembly.exe
```

Aşağıdaki komut, montajlarda `myAssembly1.exe` kaldırıcı bileşenleri yürütür `myAssembly2.exe`ve.

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

`/u` Seçeneğin komut satırındaki konumu önemli olmadığından, bu aşağıdaki komuta eşdeğerdir.

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

Aşağıdaki komut montajcıları derlemede `myAssembly.exe` yürütür ve ilerleme bilgilerinin . `myLog.InstallLog`

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

Aşağıdaki komut, montajcıları derlemede `myAssembly.exe`yürütür, ilerleme bilgilerinin sistem `myLog.InstallLog`kayıt defterine yazılması `/reg` gerektiğini belirtir ve yüklemecilerin özel seçeneğini kullanır.

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

Aşağıdaki komut montajcıları derlemede `myAssembly.exe`yürütür, kullanıcının e-posta adresini belirtmek için yükleyicinin özel `/email` seçeneğini kullanır ve günlük dosyasına çıktıyı bastırır.

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

`myAssembly.exe` Aşağıdaki komut için yükleme ilerleme `myLog.InstallLog` yazar ve `myTestAssembly.exe` için `myTestLog.InstallLog`ilerleme yazar.

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.Install>
- [Araçlar](index.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
