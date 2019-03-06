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
ms.openlocfilehash: d578381718dc5cae8c021d2ba247073a93283bc4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359841"
---
# <a name="installutilexe-installer-tool"></a>Installutil.exe (Yükleme Aracı)

Yükleyici aracı, yükleyici bileşenlerini belirli derlemelerde yürüterek sunucu kaynaklarını yüklemenize ve kaldırmanıza olanak tanıyan bir komut satırı aracıdır. Bu araç, alanındaki sınıflarla birlikte çalışır. <xref:System.Configuration.Install> ad alanı.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için Visual Studio (veya Windows 7'de Visual Studio komut istemi) için geliştirici Komut İstemi'ni kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

#### <a name="parameters"></a>Parametreler

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`assembly`|Yükleyici bileşenlerinin yürütüleceği derlemenin dosya adı. Kullanarak derlemenin tanımlayıcı adını belirtmek istiyorsanız bu parametreyi atlarsanız `/AssemblyName` seçeneği.|

<a name="options"></a>

## <a name="options"></a>Seçenekler

|Seçenek|Açıklama|
|------------|-----------------|
|`/h[elp]`<br /><br /> -veya-<br /><br /> `/?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|
|`/help` *Derleme*<br /><br /> -veya-<br /><br /> `/?` *Derleme*|InstallUtil.exe'ye ilişkin komut sözdizimi ve seçeneklerin yanı sıra, belirtilen derleme içinde tek tek yükleyiciler tarafından tanınan ek seçenekleri görüntüler. Bu seçenek her yükleyici tarafından döndürülen metni ekler <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliğini InstallUtil.exe Yardım metni.|
|`/AssemblyName` "*assemblyName*<br /><br /> ,Version=*major.minor.build.revision*<br /><br /> , Culture =*yerel ayar*<br /><br /> ,PublicKeyToken=*publicKeyToken*"|Bir derlemenin, genel derleme önbelleğine kaydedilmesi gereken tanımlayıcı adını belirtir. Derleme adı, derlemenin sürüm, kültür ve genel anahtar belirteciyle birlikte belirtilmelidir. Tam olarak belirtilen ad, tırnak işareti içine alınmalıdır.<br /><br /> Örneğin, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" tam olaralk belirtilmiş bir derleme adıdır.|
|`/InstallStateDir=[` *DizinAdı* `]`|Derlemeyi yüklemek için kullanılan verileri içeren .InstallState dosyasının dizinini içerir. Varsayılan değer, derlemeyi içeren dizindir.|
|`/LogFile=`[*filename*]|Yükleme ilerlemesinin kaydedildiği günlük dosyasının adını belirtir. Varsayılan olarak, `/LogFile` seçeneği atlanırsa, adlı bir günlük dosyası *assemblyname*. InstallLog oluşturulur. Varsa *filename* olan atlanırsa, günlük dosyası oluşturulur.|
|`/LogToConsole`={`true`&#124;`false`}|Varsa `true`, konsola çıkışı görüntüler. Varsa `false` (varsayılan), konsola çıkışı bastırır.|
|`/ShowCallStack`|Yükleme sırasında herhangi bir noktada bir özel durum oluşursa, çağrı yığınını günlük dosyana çıkış olarak aktarır.|
|`/u`[`ninstall`]|Belirtilen derlemeleri kaldırır. Diğer seçeneklerin tersine `/u` seçeneğin komut satırında göründüğü bağımsız olarak tüm derlemelere uygulanır.|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a>Ek Yükleyici Seçenekleri

Bir derlemede kullanılan her bir yükleyici listelenenlere olarak seçenekleri tanıyabilir [seçenekleri](#options) bölümü. Bu seçenekler hakkında bilgi edinmek için InstallUtil.exe derlemelerin yollarıyla komut satırı ile birlikte çalışan `/?` veya `/help` seçeneği. Bu seçenekleri belirtmek için, bunları, InstallUtil.exe tarafından tanınan seçeneklerin yanı sıra komut satırına ekleyebilirsiniz.

> [!NOTE]
> Tarafından döndürülen tek tek yükleyici bileşenleri tarafından desteklenen seçeneklerle ilgili Yardım metni <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliği. Komut satırına girilen ayrı ayrı seçenekler programlı olarak erişilebilir <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> özelliği.

Tüm seçenekler ve komut satırı parametreleri yükleme günlük dosyasına yazılır. Ancak, kullanırsanız `/Password` bazı yükleyici bileşenleri tarafından tanınan parametre, parola bilgisi sekiz yıldız işaretiyle (*) değiştirilir ve günlük dosyasında görünmez.

> [!IMPORTANT]
> Bazı durumlarda, yükleyiciye geçirilen ve varsayılan olarak düz bir metin günlüğü dosyasına yazılan, hassas veya kişisel olarak tanımlanabilir bilgiler içerebilir. Bu davranışı engellemek için günlük dosyasını belirterek gizleyebilirsiniz `/LogFile=` (olmadan *filename* bağımsız değişkeni) sonra komut satırında Installutil.exe.

## <a name="remarks"></a>Açıklamalar

.NET Framework uygulamaları, uygulama dağıtıldığında oluşturulması gereken ileti kuyrukları, olay günlükleri ve performans sayaçları gibi geleneksel program dosyalarından ve ilişkili kaynaklardan oluşur. Uygulamanız yüklendiğinde bu kaynakları oluşturmak ve uygulamanız kaldırıldığında kaldırmak için, bir derlemenin yükleyici bileşenlerini kullanabilirsiniz. Installutil.exe, bu yükleyici bileşenlerini algılar ve çalıştırır.

Aynı komut satırında birden çok derleme belirtebilirsiniz. Derleme adından önce gelen herhangi bir seçenek o derlemenin yüklemesine uygulanır. Dışında `/u` ve `/AssemblyName`, Seçenekler birikmelidir, ancak geçersiz kılınabilir. Diğer bir deyişle, bir derleme için belirtilen seçenekler, seçenek yeni bir değerle belirtilmediği sürece sonraki tüm derlemelere uygulanır.

Installutil.exe'yi herhangi bir seçenek belirtmeden bir derlemeye yönelik olarak çalıştırırsanız, aşağıdaki üç dosyayı derlemenin dizinine yerleştirir:

- InstallUtil.InstallLog - Yükleme ilerlemesinin genel bir açıklamasını içerir.

- *AssemblyName*. InstallLog - yükleme işleminin kaydetme aşamasına özel bilgiler içerir. Kaydetme aşaması hakkında daha fazla bilgi için bkz. <xref:System.Configuration.Install.Installer.Commit%2A> yöntemi.

- *AssemblyName*. InstallState - derlemeyi kaldırmak için kullanılan verileri içerir.

InstallUtil.exe belirtilen derlemeleri incelemek ve tüm bulmak için yansıtma kullanır <xref:System.Configuration.Install.Installer> sahip türleri <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> özniteliğini `true`. Araç ardından yürütür <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> veya <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> yöntemi her bir örneği üzerinde <xref:System.Configuration.Install.Installer> türü. Installutil.exe, yüklemeyi işlemsel bir şekilde gerçekleştirir; yani, derlemelerden birisi yüklenemezse, diğer tüm derlemelerin yüklemelerini geri alır. Kaldırma, işlemsel değildir.

Installutil.exe, gecikme imzalı derlemeleri yükleyemez veya kaldıramaz, fakat tanımlayıcı adlı derlemeleri yükleyebilir veya kaldırabilir.

.NET Framework sürüm 2.0 ile başlayarak, ortak dil çalışma zamanının (CLR) 32 bit sürümü Yükleyici aracının yalnızca 32 bit sürümüyle birlikte sevk edilir, fakat CLR'nin 64 bit sürümü Yükleyici aracının hem 32 bit hem de 64 bit sürümleriyle birlikte sevk edilir. 64 bit CLR kullanırken, 32 bit derlemeleri yüklemek için 32 bit Yükleyici aracını, 64 bit ve Microsoft ara dil (MSIL) derlemelerini yüklemek içinse 64 bit Yükleyici aracını kullanın. Yükleyici aracının her iki sürümü de aynı şekilde davranır.

Installutil.exe C++ derleyicisi tarafından üretilen gömülü doğal kodu tanıyamayacağından, C++ kullanarak oluşturulan bir Windows hizmetini dağıtmak için Installutil.exe'yi kullanamazsınız. Gibi bir C++ Windows hizmetini Installutil.exe, bir özel durum ile dağıtmayı denerseniz <xref:System.BadImageFormatException> oluşturulur. Bu senaryoyla çalışmak için, hizmet kodunu bir C++ modülüne taşıyın ve sonra yükleyici nesnesini C# veya Visual Basic'te yazın.

## <a name="examples"></a>Örnekler

Aşağıdaki komut, komut sözdiziminin bir açıklamasını ve InstallUtil.exe'ye ilişkin seçenekleri görüntüler.

```console
installutil /?
```

Aşağıdaki komut, komut sözdiziminin bir açıklamasını ve InstallUtil.exe'ye ilişkin seçenekleri görüntüler. Bir açıklama ve deki yükleyici bileşenleri tarafından desteklenen seçeneklerin bir listesini de görüntüler `myAssembly.exe` yükleyicinin Yardım metni atandıysa <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> özelliği.

```console
installutil /? myAssembly.exe
```

Aşağıdaki komutu derlemesindeki yükleyici bileşenlerini yürütür `myAssembly.exe`.

```console
installutil myAssembly.exe
```

Aşağıdaki komut, kullanarak bir derlemede yükleyici bileşenlerini yürütür `/AssemblyName` anahtarı ve bir tam adı.

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Aşağıdaki komut, dosya adıyla belirtilen bir derlemede ve tanımlayıcı adla belirtilen bir derlemede yükleyici bileşenlerini yürütür. Dosya adıyla belirtilen tüm derlemelerin tanımlayıcı adla komut satırında belirtilen derlemeleri çünkü gelmelidir Not `/AssemblyName` seçeneği geçersiz.

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Aşağıdaki komut, derlemesindeki kaldırıcı bileşenlerini yürütür `myAssembly.exe`.

```console
installutil /u myAssembly.exe
```

Aşağıdaki komut, derlemelerde kaldırıcı bileşenlerini yürütür `myAssembly1.exe` ve `myAssembly2.exe`.

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

Çünkü konumunu `/u` komut satırı seçeneği önemli değildir, bu aşağıdaki komuta denktir.

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

Aşağıdaki komutu derlemesindeki yükleyicileri yürütür `myAssembly.exe` ve ilerleme bilgilerinin yazılacağı belirtir `myLog.InstallLog`.

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

Aşağıdaki komutu derlemesindeki yükleyicileri yürütür `myAssembly.exe`, ilerleme durumu bilgileri için yazılması gerektiğini belirtir `myLog.InstallLog`ve özel kullanan `/reg` sisteme güncelleştirmeler yapılması gerektiğini belirtmek için seçeneği kayıt defteri.

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

Aşağıdaki komutu derlemesindeki yükleyicileri yürütür `myAssembly.exe`, kullandığı yükleyicinin özel `/email` kullanıcının e-posta adresini belirtmek için seçeneği ve günlük dosyasına çıkışı bastırır.

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

Yükleme ilerleme durumu için aşağıdaki komutu Yazar `myAssembly.exe` için `myLog.InstallLog` ve ilerleme durumunu yazan `myTestAssembly.exe` için `myTestLog.InstallLog`.

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.Install>
- [Araçlar](../../../docs/framework/tools/index.md)
- [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
