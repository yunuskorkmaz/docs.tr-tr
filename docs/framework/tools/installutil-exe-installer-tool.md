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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ad0497bd5303dc4113dbb7b8078c70cb044cc95
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044536"
---
# <a name="installutilexe-installer-tool"></a>Installutil.exe (Yükleme Aracı)

Yükleyici aracı, yükleyici bileşenlerini belirli derlemelerde yürüterek sunucu kaynaklarını yüklemenize ve kaldırmanıza olanak tanıyan bir komut satırı aracıdır. Bu araç, <xref:System.Configuration.Install> ad alanındaki sınıflarla birlikte çalışmaktadır.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

## <a name="parameters"></a>Parametreler

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`assembly`|Yükleyici bileşenlerinin yürütüleceği derlemenin dosya adı. `/AssemblyName` Seçeneğini kullanarak derlemenin tanımlayıcı adını belirtmek istiyorsanız bu parametreyi atlayın.|

<a name="options"></a>

## <a name="options"></a>Seçenekler

|Seçenek|Açıklama|
|------------|-----------------|
|`/h[elp]`<br /><br /> -veya-<br /><br /> `/?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|
|`/help`*derleme*<br /><br /> -veya-<br /><br /> `/?`*derleme*|InstallUtil.exe'ye ilişkin komut sözdizimi ve seçeneklerin yanı sıra, belirtilen derleme içinde tek tek yükleyiciler tarafından tanınan ek seçenekleri görüntüler. Bu seçenek, her bir yükleyici bileşeninin <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliği tarafından döndürülen metni InstallUtil. exe ' nin yardım metnine ekler.|
|`/AssemblyName`"*AssemblyName*<br /><br /> , Sürüm =*ana. ikincil. derleme. düzeltme*<br /><br /> , Kültür =*yerel ayar*<br /><br /> ,PublicKeyToken=*publicKeyToken*"|Bir derlemenin, genel derleme önbelleğine kaydedilmesi gereken tanımlayıcı adını belirtir. Derleme adı, derlemenin sürüm, kültür ve genel anahtar belirteciyle birlikte belirtilmelidir. Tam olarak belirtilen ad, tırnak işareti içine alınmalıdır.<br /><br /> Örneğin, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" tam olaralk belirtilmiş bir derleme adıdır.|
|`/InstallStateDir=[`*DirectoryName*`]`|Derlemeyi yüklemek için kullanılan verileri içeren .InstallState dosyasının dizinini içerir. Varsayılan değer, derlemeyi içeren dizindir.|
|`/LogFile=`[*dosya adı*]|Yükleme ilerlemesinin kaydedildiği günlük dosyasının adını belirtir. Varsayılan `/LogFile` olarak, seçeneği atlanırsa *AssemblyName*adlı bir günlük dosyası. InstallLog oluşturuldu. *Dosya adı* atlanırsa, günlük dosyası oluşturulmaz.|
|`/LogToConsole`={`true`&#124;`false`}|`true`, Çıktıyı konsola görüntüler. `false` (Varsayılan), çıktıyı konsola bastırır.|
|`/ShowCallStack`|Yükleme sırasında herhangi bir noktada bir özel durum oluşursa, çağrı yığınını günlük dosyana çıkış olarak aktarır.|
|`/u`[`ninstall`]|Belirtilen derlemeleri kaldırır. Diğer seçeneklerin aksine, `/u` seçeneğin komut satırında göründüğü yere bakılmaksızın tüm derlemeler için geçerlidir.|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a>Ek Yükleyici Seçenekleri

Bir derlemede kullanılan bireysel yükleyiciler [Seçenekler](#options) bölümünde listelenenlere ek olarak seçenekleri tanıyabilir. Bu seçenekler hakkında bilgi edinmek için, komut satırındaki derlemelerin yollarıyla birlikte `/?` InstallUtil. exe ' yi veya `/help` seçeneğini çalıştırın. Bu seçenekleri belirtmek için, bunları, InstallUtil.exe tarafından tanınan seçeneklerin yanı sıra komut satırına ekleyebilirsiniz.

> [!NOTE]
> Ayrı yükleyici bileşenleri tarafından desteklenen seçeneklerde yardım metni, <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliği tarafından döndürülür. Komut satırına girilen tek tek seçeneklere <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> özelliğinden programlı olarak erişilebilir.

Tüm seçenekler ve komut satırı parametreleri yükleme günlük dosyasına yazılır. Ancak, bazı yükleyici bileşenleri tarafından `/Password` tanınan parametresini kullanırsanız, parola bilgileri sekiz yıldız işaretiyle (*) değişir ve günlük dosyasında görünmez.

> [!IMPORTANT]
> Bazı durumlarda, yükleyiciye geçirilen ve varsayılan olarak düz bir metin günlüğü dosyasına yazılan, hassas veya kişisel olarak tanımlanabilir bilgiler içerebilir. Bu davranışı önlemek için, komut satırında InstallUtil. exe ' den `/LogFile=` sonra ( *dosya adı* olmadan) öğesini belirterek günlük dosyasını bastırın.

## <a name="remarks"></a>Açıklamalar

.NET Framework uygulamaları, uygulama dağıtıldığında oluşturulması gereken ileti kuyrukları, olay günlükleri ve performans sayaçları gibi geleneksel program dosyalarından ve ilişkili kaynaklardan oluşur. Uygulamanız yüklendiğinde bu kaynakları oluşturmak ve uygulamanız kaldırıldığında kaldırmak için, bir derlemenin yükleyici bileşenlerini kullanabilirsiniz. Installutil.exe, bu yükleyici bileşenlerini algılar ve çalıştırır.

Aynı komut satırında birden çok derleme belirtebilirsiniz. Derleme adından önce gelen herhangi bir seçenek o derlemenin yüklemesine uygulanır. `/u` Ve`/AssemblyName`dışında, Seçenekler birikimli ancak geçersiz kılınabilir. Diğer bir deyişle, bir derleme için belirtilen seçenekler, seçenek yeni bir değerle belirtilmediği sürece sonraki tüm derlemelere uygulanır.

Installutil.exe'yi herhangi bir seçenek belirtmeden bir derlemeye yönelik olarak çalıştırırsanız, aşağıdaki üç dosyayı derlemenin dizinine yerleştirir:

- InstallUtil.InstallLog - Yükleme ilerlemesinin genel bir açıklamasını içerir.

- *AssemblyName*. InstallLog-yükleme işleminin kaydetme aşamasına özgü bilgileri Içerir. Tamamlama aşaması hakkında daha fazla bilgi için, bkz <xref:System.Configuration.Install.Installer.Commit%2A> . yöntemi.

- *AssemblyName*. InstallState-derlemeyi kaldırmak için kullanılan verileri Içerir.

InstallUtil. exe, <xref:System.Configuration.Install.Installer> <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> belirtilen derlemeleri incelemek ve özniteliği olarak `true`ayarlanmış tüm türleri bulmak için yansıma kullanır. Araç daha sonra <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> <xref:System.Configuration.Install.Installer> türü her örneği üzerinde <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> ya da yöntemini yürütür. Installutil.exe, yüklemeyi işlemsel bir şekilde gerçekleştirir; yani, derlemelerden birisi yüklenemezse, diğer tüm derlemelerin yüklemelerini geri alır. Kaldırma, işlemsel değildir.

Installutil.exe, gecikme imzalı derlemeleri yükleyemez veya kaldıramaz, fakat tanımlayıcı adlı derlemeleri yükleyebilir veya kaldırabilir.

.NET Framework sürüm 2.0 ile başlayarak, ortak dil çalışma zamanının (CLR) 32 bit sürümü Yükleyici aracının yalnızca 32 bit sürümüyle birlikte sevk edilir, fakat CLR'nin 64 bit sürümü Yükleyici aracının hem 32 bit hem de 64 bit sürümleriyle birlikte sevk edilir. 64 bit CLR kullanırken, 32 bit derlemeleri yüklemek için 32 bit Yükleyici aracını, 64 bit ve Microsoft ara dil (MSIL) derlemelerini yüklemek içinse 64 bit Yükleyici aracını kullanın. Yükleyici aracının her iki sürümü de aynı şekilde davranır.

Installutil.exe C++ derleyicisi tarafından üretilen gömülü doğal kodu tanıyamayacağından, C++ kullanarak oluşturulan bir Windows hizmetini dağıtmak için Installutil.exe'yi kullanamazsınız. InstallUtil. exe ile bir C++ Windows hizmeti dağıtmaya çalışırsanız, gibi bir özel durum <xref:System.BadImageFormatException> oluşturulur. Bu senaryoyla çalışmak için, hizmet kodunu bir C++ modülüne taşıyın ve sonra yükleyici nesnesini C# veya Visual Basic'te yazın.

## <a name="examples"></a>Örnekler

Aşağıdaki komut, komut sözdiziminin bir açıklamasını ve InstallUtil.exe'ye ilişkin seçenekleri görüntüler.

```console
installutil /?
```

Aşağıdaki komut, komut sözdiziminin bir açıklamasını ve InstallUtil.exe'ye ilişkin seçenekleri görüntüler. Ayrıca, `myAssembly.exe` <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> yükleyicinin özelliğine yardım metni atanmışsa, içindeki yükleyici bileşenleri tarafından desteklenen seçeneklerin bir açıklamasını ve listesini görüntüler.

```console
installutil /? myAssembly.exe
```

Aşağıdaki komut, derlemede `myAssembly.exe`yükleyici bileşenlerini yürütür.

```console
installutil myAssembly.exe
```

Aşağıdaki komut, `/AssemblyName` anahtarı ve tam nitelikli adı kullanarak bir derlemede yükleyici bileşenlerini yürütür.

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Aşağıdaki komut, dosya adıyla belirtilen bir derlemede ve tanımlayıcı adla belirtilen bir derlemede yükleyici bileşenlerini yürütür. `/AssemblyName` Seçenek geçersiz kılınamadığından, dosya adı tarafından belirtilen tüm derlemelerin komut satırında tanımlayıcı ad tarafından belirtilen derlemelerden önce gelmelidir olduğuna unutmayın.

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Aşağıdaki komut derlemedeki `myAssembly.exe`Uninstaller bileşenlerini yürütür.

```console
installutil /u myAssembly.exe
```

Aşağıdaki komut, derlemelerdeki `myAssembly1.exe` ve `myAssembly2.exe`yükleyicideki Uninstaller bileşenlerini yürütür.

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

`/u` Seçeneğinin komut satırındaki konumu önemli olmadığından, bu, aşağıdaki komuta eşdeğerdir.

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

Aşağıdaki komut, derlemede `myAssembly.exe` yükleyicileri yürütür ve ilerleme bilgilerinin `myLog.InstallLog`yazıldığını belirtir.

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

Aşağıdaki komut derlemede `myAssembly.exe`yükleyicileri yürütür, ilerleme bilgilerinin üzerine `myLog.InstallLog`yazılması gerektiğini belirtir ve güncelleştirmelerin sisteme yapılması gerektiğini belirtmek için yükleyicilerin özel `/reg` seçeneğini kullanır defteri.

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

Aşağıdaki komut derlemede `myAssembly.exe`yükleyicileri yürütür, kullanıcının e-posta adresini belirtmek için yükleyicinin özel `/email` seçeneğini kullanır ve günlük dosyasına çıktıyı bastırır.

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

Aşağıdaki komut, `myAssembly.exe` için yükleme ilerleme durumunu `myLog.InstallLog` yazar `myTestAssembly.exe` ve için ilerleme durumunu `myTestLog.InstallLog`yazar.

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.Install>
- [Araçlar](index.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
