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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105068"
---
# <a name="installutilexe-installer-tool"></a>Installutil.exe (Yükleme Aracı)

Yükleyici aracı, yükleyici bileşenlerini belirli derlemelerde yürüterek sunucu kaynaklarını yüklemenize ve kaldırmanıza olanak tanıyan bir komut satırı aracıdır. Bu araç <xref:System.Configuration.Install> ad alanındaki sınıflarla birlikte çalışmaktadır.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

## <a name="parameters"></a>Parametreler

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`assembly`|Yükleyici bileşenlerinin yürütüleceği derlemenin dosya adı. `/AssemblyName` seçeneğini kullanarak derlemenin tanımlayıcı adını belirtmek istiyorsanız bu parametreyi atlayın.|

<a name="options"></a>

## <a name="options"></a>Seçenekler

|Seçenek|Açıklama|
|------------|-----------------|
|`/h[elp]`<br /><br /> veya<br /><br /> `/?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|
|`/help` *derlemesi*<br /><br /> veya<br /><br /> `/?` *derlemesi*|InstallUtil.exe'ye ilişkin komut sözdizimi ve seçeneklerin yanı sıra, belirtilen derleme içinde tek tek yükleyiciler tarafından tanınan ek seçenekleri görüntüler. Bu seçenek, her bir yükleyici bileşeninin <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliği tarafından döndürülen metni InstallUtil. exe ' nin yardım metnine ekler.|
|`/AssemblyName` "*AssemblyName*<br /><br /> , Sürüm =*ana. ikincil. derleme. düzeltme*<br /><br /> , Kültür =*yerel ayar*<br /><br /> , PublicKeyToken =*PublicKeyToken*"|Bir derlemenin, genel derleme önbelleğine kaydedilmesi gereken tanımlayıcı adını belirtir. Derleme adı, derlemenin sürüm, kültür ve genel anahtar belirteciyle birlikte belirtilmelidir. Tam olarak belirtilen ad, tırnak işareti içine alınmalıdır.<br /><br /> Örneğin, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" tam olaralk belirtilmiş bir derleme adıdır.|
|`/InstallStateDir=[` *directoryName* `]`|Derlemeyi yüklemek için kullanılan verileri içeren .InstallState dosyasının dizinini içerir. Varsayılan değer, derlemeyi içeren dizindir.|
|`/LogFile=`[*filename*]|Yükleme ilerlemesinin kaydedildiği günlük dosyasının adını belirtir. Varsayılan olarak, `/LogFile` seçeneği atlanmışsa, *AssemblyName*adlı bir günlük dosyası. InstallLog oluşturuldu. *Dosya adı* atlanırsa, günlük dosyası oluşturulmaz.|
|`/LogToConsole`= {`true`&#124;`false`}|`true`, çıktıyı konsola görüntüler. `false` (varsayılan), konsola çıktıyı bastırır.|
|`/ShowCallStack`|Yükleme sırasında herhangi bir noktada bir özel durum oluşursa, çağrı yığınını günlük dosyana çıkış olarak aktarır.|
|`/u`[`ninstall`]|Belirtilen derlemeleri kaldırır. Diğer seçeneklerin aksine, `/u` seçeneğin komut satırında nerede göründüğünden bağımsız olarak tüm derlemeler için geçerlidir.|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a>Ek Yükleyici Seçenekleri

Bir derlemede kullanılan bireysel yükleyiciler [Seçenekler](#options) bölümünde listelenenlere ek olarak seçenekleri tanıyabilir. Bu seçenekler hakkında bilgi edinmek için, komut satırındaki derlemelerin yollarıyla birlikte InstallUtil. exe ' yi `/?` veya `/help` seçeneğiyle çalıştırın. Bu seçenekleri belirtmek için, bunları, InstallUtil.exe tarafından tanınan seçeneklerin yanı sıra komut satırına ekleyebilirsiniz.

> [!NOTE]
> Bireysel yükleyici bileşenleri tarafından desteklenen seçeneklerde yardım metni <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliği tarafından döndürülür. Komut satırına girilen tek tek seçeneklere <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> özelliğinden programlı olarak erişilebilir.

Tüm seçenekler ve komut satırı parametreleri yükleme günlük dosyasına yazılır. Ancak, bazı yükleyici bileşenleri tarafından tanınan `/Password` parametresini kullanırsanız, parola bilgileri sekiz yıldız işaretiyle (*) değişir ve günlük dosyasında görünmez.

> [!IMPORTANT]
> Bazı durumlarda, yükleyiciye geçirilen ve varsayılan olarak düz bir metin günlüğü dosyasına yazılan, hassas veya kişisel olarak tanımlanabilir bilgiler içerebilir. Bu davranışı önlemek için, komut satırında InstallUtil. exe sonrasında `/LogFile=` ( *dosya adı* olmadan) öğesini belirterek günlük dosyasını gizleyebilirsiniz.

## <a name="remarks"></a>Açıklamalar

.NET Framework uygulamaları, uygulama dağıtıldığında oluşturulması gereken ileti kuyrukları, olay günlükleri ve performans sayaçları gibi geleneksel program dosyalarından ve ilişkili kaynaklardan oluşur. Uygulamanız yüklendiğinde bu kaynakları oluşturmak ve uygulamanız kaldırıldığında kaldırmak için, bir derlemenin yükleyici bileşenlerini kullanabilirsiniz. Installutil.exe, bu yükleyici bileşenlerini algılar ve çalıştırır.

Aynı komut satırında birden çok derleme belirtebilirsiniz. Derleme adından önce gelen herhangi bir seçenek o derlemenin yüklemesine uygulanır. `/u` ve `/AssemblyName`hariç, Seçenekler birikimli ancak geçersiz kılınabilir. Diğer bir deyişle, bir derleme için belirtilen seçenekler, seçenek yeni bir değerle belirtilmediği sürece sonraki tüm derlemelere uygulanır.

Installutil.exe'yi herhangi bir seçenek belirtmeden bir derlemeye yönelik olarak çalıştırırsanız, aşağıdaki üç dosyayı derlemenin dizinine yerleştirir:

- InstallUtil.InstallLog - Yükleme ilerlemesinin genel bir açıklamasını içerir.

- *AssemblyName*. InstallLog-yükleme işleminin kaydetme aşamasına özgü bilgileri Içerir. Tamamlama aşaması hakkında daha fazla bilgi için <xref:System.Configuration.Install.Installer.Commit%2A> yöntemine bakın.

- *AssemblyName*. InstallState-derlemeyi kaldırmak için kullanılan verileri Içerir.

InstallUtil. exe, belirtilen derlemeleri incelemek ve <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> özniteliği `true`olarak ayarlanan tüm <xref:System.Configuration.Install.Installer> türlerini bulmak için yansıma kullanır. Araç daha sonra <xref:System.Configuration.Install.Installer> türünün her örneğindeki <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> veya <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> yöntemini yürütür. Installutil.exe, yüklemeyi işlemsel bir şekilde gerçekleştirir; yani, derlemelerden birisi yüklenemezse, diğer tüm derlemelerin yüklemelerini geri alır. Kaldırma, işlemsel değildir.

Installutil.exe, gecikme imzalı derlemeleri yükleyemez veya kaldıramaz, fakat tanımlayıcı adlı derlemeleri yükleyebilir veya kaldırabilir.

.NET Framework sürüm 2.0 ile başlayarak, ortak dil çalışma zamanının (CLR) 32 bit sürümü Yükleyici aracının yalnızca 32 bit sürümüyle birlikte sevk edilir, fakat CLR'nin 64 bit sürümü Yükleyici aracının hem 32 bit hem de 64 bit sürümleriyle birlikte sevk edilir. 64 bit CLR kullanırken, 32 bit derlemeleri yüklemek için 32 bit Yükleyici aracını, 64 bit ve Microsoft ara dil (MSIL) derlemelerini yüklemek içinse 64 bit Yükleyici aracını kullanın. Yükleyici aracının her iki sürümü de aynı şekilde davranır.

Installutil.exe C++ derleyicisi tarafından üretilen gömülü doğal kodu tanıyamayacağından, C++ kullanarak oluşturulan bir Windows hizmetini dağıtmak için Installutil.exe'yi kullanamazsınız. InstallUtil. exe ile bir C++ Windows hizmeti dağıtmaya çalışırsanız, <xref:System.BadImageFormatException> gibi bir özel durum oluşturulur. Bu senaryoyla çalışmak için, hizmet kodunu bir C++ modülüne taşıyın ve sonra yükleyici nesnesini C# veya Visual Basic'te yazın.

## <a name="examples"></a>Örnekler

Aşağıdaki komut, komut sözdiziminin bir açıklamasını ve InstallUtil.exe'ye ilişkin seçenekleri görüntüler.

```console
installutil /?
```

Aşağıdaki komut, komut sözdiziminin bir açıklamasını ve InstallUtil.exe'ye ilişkin seçenekleri görüntüler. Ayrıca, yükleyicinin <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliğine yardım metni atanmışsa `myAssembly.exe` içindeki yükleyici bileşenleri tarafından desteklenen seçeneklerin açıklaması ve listesi görüntülenir.

```console
installutil /? myAssembly.exe
```

Aşağıdaki komut `myAssembly.exe`derlemede yükleyici bileşenlerini yürütür.

```console
installutil myAssembly.exe
```

Aşağıdaki komut, `/AssemblyName` anahtarını ve tam nitelikli adı kullanarak bir derlemede yükleyici bileşenlerini yürütür.

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Aşağıdaki komut, dosya adıyla belirtilen bir derlemede ve tanımlayıcı adla belirtilen bir derlemede yükleyici bileşenlerini yürütür. `/AssemblyName` seçeneği geçersiz kılınamadığından, dosya adı tarafından belirtilen tüm derlemelerin komut satırında tanımlayıcı ad tarafından belirtilen derlemelerden önce kullanılması gerektiğini unutmayın.

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Aşağıdaki komut `myAssembly.exe`derlemede UnInstaller bileşenlerini yürütür.

```console
installutil /u myAssembly.exe
```

Aşağıdaki komut `myAssembly1.exe` derlemelerdeki Uninstaller bileşenlerini yürütür ve `myAssembly2.exe`.

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

Komut satırındaki `/u` seçeneğinin konumu önemli olmadığından, bu, aşağıdaki komuta eşdeğerdir.

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

Aşağıdaki komut, derleme `myAssembly.exe` yükleyicileri yürütür ve ilerleme bilgilerinin `myLog.InstallLog`yazıldığını belirtir.

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

Aşağıdaki komut, derleme `myAssembly.exe`yükleyicilerini yürütür, ilerleme bilgilerinin `myLog.InstallLog`yazılması gerektiğini belirtir ve yükleyicilerin sistem kayıt defterine yapılması gerektiğini belirtmek için yükleyicileri özel `/reg` seçeneğini kullanır.

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

Aşağıdaki komut, derleme `myAssembly.exe`yükleyicileri yürütür, kullanıcının e-posta adresini belirtmek için yükleyicinin özel `/email` seçeneğini kullanır ve günlük dosyasına çıktıyı bastırır.

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

Aşağıdaki komut `myAssembly.exe` için yükleme ilerlemesini `myLog.InstallLog` ve `myTestAssembly.exe` ilerleme durumunu `myTestLog.InstallLog`olarak yazar.

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.Install>
- [Araçlar](index.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
