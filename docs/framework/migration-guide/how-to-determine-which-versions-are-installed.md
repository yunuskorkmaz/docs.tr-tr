---
title: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme
description: Windows kayıt defterini sorgulayarak .NET Framework'ün hangi sürümlerinin makineye yüklenirolduğunu algılamak için kod, regedit.exe veya PowerShell'i kullanın.
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: 8469f977c6ed9691c81a2a8354935557b5c27171
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77093843"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Nasıl yapılır: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme

Kullanıcılar bilgisayarlarına .NET Framework'ün birden çok sürümü [yükleyebilir](../install/index.md) ve çalıştırabilir. Uygulamanızı geliştirdiğinizde veya dağıttığınızda, kullanıcının bilgisayarında hangi .NET Framework sürümlerinin yüklü olduğunu bilmeniz gerekebilir. Kayıt defteri, bilgisayara yüklenen .NET Framework sürümlerinin bir listesini içerir.

.NET Framework, ayrı olarak sürümlenmiş iki ana bileşenden oluşur:

- Uygulamalarınız için işlevselliği sağlayan türler ve kaynaklar danoluşan derlemeler kümesi. .NET Framework ve derlemeler aynı sürüm numarasını paylaşır. Örneğin, .NET Framework sürümleri 4.5, 4.6.1 ve 4.7.2'yi içerir.

- Uygulamanızın kodunu yöneten ve çalıştıran ortak dil çalışma süresi (CLR). Tek bir CLR sürümü genellikle birden çok .NET Framework sürümünü destekler. Örneğin, CLR sürüm 4.0.30319. *xxxxx* 42000'den az olduğu *xxxxx,* .NET Framework sürümleri 4 ile 4.5.2 arasında destekler. 4.0.30319.42000'den büyük veya eşit CLR sürümü .NET Framework 4.6 ile başlayan .NET Framework sürümlerini destekler.

Topluluk tarafından korunan araçlar, hangi .NET Framework sürümlerinin yüklü olduğunu algılamaya yardımcı olmak için kullanılabilir:

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  Bir .NET 2.0 komut satırı aracı.

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  PowerShell 2.0 modülü.

.NET Framework'ün her sürümü için yüklenen güncelleştirmeleri algılama hakkında bilgi için [bkz: Hangi .NET Framework güncelleştirmelerinin yüklü olduğunu belirleyin.](how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="detect-net-framework-45-and-later-versions"></a>.NET Framework 4.5 ve sonraki sürümlerini algıla

Bir makineye yüklenen .NET Framework (4.5 ve sonrası) sürümü **HKEY_LOCAL_MACHINE\\SOFTWARE\\\\Microsoft NET\\Framework\\Setup\\NDP v4 Full**adresindeki kayıt defterinde listelenmiştir. **Tam** alt anahtar eksikse, .NET Framework 4.5 veya üzeri yüklü değildir.

> [!NOTE]
> Kayıt defteri yolundaki **NET Framework Setup** alt anahtarı bir dönemle *başlamaz.*

Kayıt defterindeki **Sürüm** REG_DWORD değeri .NET Framework yüklü sürümünü temsil eder.

<a name="version_table"></a>

| .NET Framework sürümü | Serbest **Bırakma** Değeri |
| ---------------------- | -------------------------- |
| .NET Framework 4.5     | Tüm Windows işletim sistemleri: 378389 |
| .NET Framework 4.5.1   | Windows 8.1 ve Windows Server 2012 R2: 378675<br />Diğer tüm Windows işletim sistemlerinde: 378758 |
| .NET Framework 4.5.2   | Tüm Windows işletim sistemleri: 379893 |
| .NET Framework 4.6     | Windows 10 üzerinde: 393295<br />Diğer tüm Windows işletim sistemlerinde: 393297 |
| .NET Framework 4.6.1   | Windows 10 Kasım Güncelleştirme sistemleri: 394254<br />Diğer tüm Windows işletim sistemlerinde (Windows 10 dahil): 394271 |
| .NET Framework 4.6.2   | Windows 10 Anniversary Update ve Windows Server 2016 tarihinde: 394802<br />Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 394806 |
|  .NET Framework 4.7     | Windows 10 Creators Update:460798<br />Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 460805 |
| .NET Çerçeve 4.7.1   | Windows 10 Fall Creators Update ve Windows Server'da sürüm 1709: 461308<br/>Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 461310 |
|  .NET Framework 4.7.2   | Windows 10 Nisan 2018 Güncelleştirmeve Windows Server,sürüm 1803: 461808<br/>Windows dışındaki tüm Windows işletim sistemlerinde 10 Nisan 2018 Güncelleştirmesi ve Windows Server, sürüm 1803: 461814 |
|  .NET Framework 4.8     | Windows 10 Mayıs 2019 Güncelleştirmesi ve Windows 10 Kasım 2019 Güncelleştirme: 528040<br/>Windows 10 ve Windows Server'da sürüm 1909: 528209<br/>Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 528049 |

### <a name="minimum-version"></a>En düşük sürüm

.NET Framework'ün *en küçük* sürümünün mevcut olup olmadığını belirlemek için, önceki tablodaki sürüm için en küçük **Sürüm** REG_DWORD değerini kullanın.

Örneğin, uygulamanız .NET Framework 4.8 veya daha sonraki bir sürüm altında çalışıyorsa, 528040'dan *büyük veya eşit* bir **sürüm** REG_DWORD değeri için sınayın.

| .NET Framework sürümü | En küçük değer |
| ---------------------- | ------------- |
| .NET Framework 4.5     | 378389 |
| .NET Framework 4.5.1   | 378675 |
| .NET Framework 4.5.2   | 379893 |
| .NET Framework 4.6     | 393295 |
| .NET Framework 4.6.1   | 394254 |
| .NET Framework 4.6.2   | 394802 |
|  .NET Framework 4.7     | 460798 |
| .NET Çerçeve 4.7.1   | 461308 |
|  .NET Framework 4.7.2   | 461808 |
|  .NET Framework 4.8     | 528040 |

### <a name="use-registry-editor"></a>Kayıt Defteri Düzenleyicisi'ni kullanma

01. **Başlat** menüsünden **Çalıştır'ı**, *regedit'i*girin ve ardından **Tamam'ı**seçin.

    Regedit çalıştırmak için yönetim kimlik bilgilerine sahip olması gerekir.

01. Kayıt Defteri Düzenleyicisi'nde aşağıdaki alt anahtarı açın: **HKEY_LOCAL_MACHINE\\YAZILIM\\Microsoft\\NET Framework\\Setup NDP\\v4\\Full**. **Tam** alt anahtar yoksa,.NET Framework 4.5 veya daha sonra yüklü değilsiniz.

01. Sürüm adlı bir REG_DWORD girişini **denetleme.** Varsa, .NET Framework 4.5 veya daha sonra yüklü. Değeri .NET Framework'ün belirli bir sürümüne karşılık gelir. Aşağıdaki şekilde, örneğin, **Release** girişinin değeri 528040'dır ve bu da .NET Framework 4.8'in sürüm anahtarıdır.

    ![.NET Framework 4.5 için kayıt defteri girişi](./media/clr-installdir.png ".NET Framework 4.5 için kayıt defteri girişi")

### <a name="use-powershell-to-check-for-a-minimum-version"></a>En az sürümü denetlemek için PowerShell'i kullanın

**HKEY_LOCAL_MACHINE\\SOFTWARE\\\\Microsoft NET Framework Setup\\NDP\\v4\\Tam** alt tutamının **Sürüm** girişinin değerini kontrol etmek için PowerShell komutlarını kullanın.

Aşağıdaki örnekler, .NET Framework 4.6.2 veya sonraki lerinin yüklü olup olmadığını belirlemek için **Yayın** girişinin değerini denetler. Bu kod `True` yüklenmişse veya `False` başka bir şekilde döndürür.

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a>Kodu kullanarak kayıt defterini sorgula

01. Windows <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> kayıt <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> defterinde **HKEY_LOCAL_MACHINE\\\\SOFTWARE\\Microsoft\\NET\\Framework\\Setup NDP v4 Tam** alt anahtarerişmek için ve yöntemleri kullanın.

    > [!IMPORTANT]
    > Çalıştırdığınız uygulama 32 bit ve 64 bit Windows'da çalışıyorsa, kayıt defteri yolları önceden listelenenden farklı olacaktır. 64-bit kayıt HKEY_LOCAL_MACHINE **\\SOFTWARE\\Wow6432Node\\ ** alt anahtar mevcuttur. Örneğin, .NET Framework 4.5'in kayıt defteri alt anahtarı **\\HKEY_LOCAL_MACHINE\\YAZıLıM\\\\Wow6432Node Microsoft NET Framework Setup\\NDP\\v4\\Full'dur.**

01. Yüklenen sürümü belirlemek için **Sürüm** REG_DWORD değerini denetleyin. İleriye dönük uyumlu olmak için [,.NET Framework sürüm tablosunda](#version_table)listelenen değerden daha büyük veya eşit bir değer olup olmadığı kontrol edin.

Aşağıdaki örnek, .NET Framework 4.5 ve yüklenen sonraki sürümleri bulmak için kayıt defterindeki **Release** girişinin değerini denetler:

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

Bu örnek, sürüm denetimi için önerilen uygulama izler:

- **Serbest bırakma** girişinin değerinin bilinen sürüm anahtarlarının değerinden büyük mü yoksa *eşit* mi olduğunu denetler.
- En son sürümden en eski sürüme kadar sırayla denetler.

## <a name="detect-net-framework-10-through-40"></a>.NET Framework 1.0 ile 4.0 arası algılama

.NET Framework'ün 1.1'den 4.0'a kadar olan her sürümü **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP'de**alt anahtar olarak listelenir. Aşağıdaki tabloda her .NET Framework sürümüne giden yolu listelemesi yer alıyor. Çoğu sürümiçin, bu sürümün `1` yüklü olduğunu belirtmek için yükleme REG_DWORD değeri vardır. **Install** Bu alt anahtarlarda, sürüm dizesi içeren **sürüm** REG_SZ değeri de vardır.

> [!NOTE]
> Kayıt defteri yolundaki **NET Framework Setup** alt anahtarı bir dönemle *başlamaz.*

| Çerçeve Sürümü  | Kayıt Defteri Alt Anahtarı | Değer |
| ------------------ | --------------- | ----- |
| 1.0                | **HKLM\\\\Yazılım\\Microsoft . NETFramework\\\\Politikası v1.0\\3705**     | **Yükle** REG_SZ eşittir`1` |
| 1.1                | **HKLM\\\\Yazılım\\Microsoft\\NET\\Çerçeve Kurulum NDP v1.1.4322**   | **Yükle** REG_DWORD eşittir`1` |
| 2,0                | **HKLM\\\\Yazılım\\Microsoft\\NET\\Çerçeve Kurulum NDP v2.0.50727**  | **Yükle** REG_DWORD eşittir`1` |
| 3,0                | **HKLM\\\\Yazılım\\Microsoft\\NET\\Çerçeve Kurulum\\NDP v3.0 Kurulum** | **YüklemeBaşarı** REG_DWORD eşittir`1` |
| 3,5                | **HKLM\\\\Yazılım\\Microsoft\\NET\\Çerçeve Kurulum NDP v3.5**        | **Yükle** REG_DWORD eşittir`1` |
| 4.0 İstemci Profili | **HKLM\\\\Yazılım\\Microsoft\\NET\\Çerçeve\\Kurulum NDP v4 İstemci**  | **Yükle** REG_DWORD eşittir`1` |
| 4.0 Tam Profil   | **HKLM\\\\Yazılım\\Microsoft\\NET\\Çerçeve\\Kurulum NDP v4 Tam**    | **Yükle** REG_DWORD eşittir`1` |

> [!IMPORTANT]
> Çalıştırdığınız uygulama 32 bit ve 64 bit Windows'da çalışıyorsa, kayıt defteri yolları önceden listelenenden farklı olacaktır. 64-bit kayıt HKEY_LOCAL_MACHINE **\\SOFTWARE\\Wow6432Node\\ ** alt anahtar mevcuttur. Örneğin, .NET Framework 3.5'in kayıt defteri alt anahtarı **HKEY_LOCAL_MACHINE\\\\YAZıLıM\\\\Wow6432Node Microsoft NET Framework Setup\\NDP\\v3.5'tir.**

.NET Framework 1.0 alt anahtarına giden kayıt yolunun diğerlerinden farklı olduğuna dikkat edin.

### <a name="use-registry-editor-older-framework-versions"></a>Kayıt Defteri Düzenleyicisi'ni kullanma (eski çerçeve sürümleri)

01. **Başlat** menüsünden **Çalıştır'ı**, *regedit'i*girin ve ardından **Tamam'ı**seçin.

    Regedit çalıştırmak için yönetim kimlik bilgilerine sahip olması gerekir.

01. Denetlemek istediğiniz sürümle eşleşen alt anahtarı açın. [Tabloyu Algıla .NET Framework 1.0 ile 4.0](#detect-net-framework-10-through-40) bölümünde kullanın.

    Aşağıdaki şekil,.NET Framework 3.5'in alt anahtarını ve **Sürüm** değerini gösterir.

    ![.NET Framework 3.5'in kayıt defteri girişi.](./media/net-4-and-earlier.png ".NET Framework 3.5 ve önceki sürümler")

### <a name="query-the-registry-using-code-older-framework-versions"></a>Kodu kullanarak kayıt defterini sorgula (eski çerçeve sürümleri)

Windows <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> kayıt defterinde **\\HKEY_LOCAL_MACHINE\\\\SOFTWARE Microsoft\\NET Framework Setup NDP** alt anahtarına erişmek için sınıfı kullanın.

> [!IMPORTANT]
> Çalıştırdığınız uygulama 32 bit ve 64 bit Windows'da çalışıyorsa, kayıt defteri yolları önceden listelenenden farklı olacaktır. 64-bit kayıt HKEY_LOCAL_MACHINE **\\SOFTWARE\\Wow6432Node\\ ** alt anahtar mevcuttur. Örneğin, .NET Framework 3.5'in kayıt defteri alt anahtarı **HKEY_LOCAL_MACHINE\\\\YAZıLıM\\\\Wow6432Node Microsoft NET Framework Setup\\NDP\\v3.5'tir.**

Aşağıdaki örnekte .NET Framework 1 ile 4 sürümleri yüklü bulur:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a>CLR sürümlerini bul

.NET Framework ile yüklenen .NET Framework CLR ayrı olarak sürülür. .NET Framework CLR sürümünü algılamanın iki yolu vardır:

- **Clrver.exe aracı**

  CLR'nin hangi sürümlerinin bilgisayara yüklendiğini belirlemek için [CLR Sürüm aracını (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) kullanın. Visual [Studio için Geliştirici Komut Komut Komut Ustem'ini](../tools/developer-command-prompt-for-vs.md) açın ve girin. `clrver`

  Örnek çıktı:

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- **Sınıf `Environment`**

  > [!IMPORTANT]
  > .NET Framework 4.5 ve sonraki sürümler <xref:System.Environment.Version%2A?displayProperty=nameWithType> için, CLR sürümünü algılamak için özelliği kullanmayın. Bunun yerine, kayıt defterini [Detect.NET Framework 4.5 ve sonraki sürümlerde](#detect-net-framework-45-and-later-versions)açıklandığı şekilde sorgula.
  
  01. Bir <xref:System.Version> <xref:System.Environment.Version?displayProperty=nameWithType> nesneyi almak için özelliği sorgula.
  
      Döndürülen `System.Version` nesne, şu anda kodu yürüten çalışma zamanının sürümünü tanımlar. Bilgisayara yüklenmiş olabilecek derleme sürümlerini veya çalışma zamanının diğer sürümlerini döndürmez.
  
      .NET Framework sürümleri 4, 4.5, 4.5.1 ve 4.5.2 için <xref:System.Version> döndürülen nesnenin dize gösterimi 4.0.30319 formuna sahiptir. *xxxxx*, *xxxxx* 42000'den az olduğu yer. .NET Framework 4.6 ve sonraki sürümler için 4.0.30319.42000 formu vardır.
  
  01. **Sürüm** nesnesini aldıktan sonra aşağıdaki gibi sorgulanın:
  
      - Büyük sürüm tanımlayıcısı için (örneğin, sürüm 4.0 için *4),* <xref:System.Version.Major%2A?displayProperty=nameWithType> özelliği kullanın.
  
      - Küçük sürüm tanımlayıcısı için (örneğin, sürüm 4.0 için *0),* <xref:System.Version.Minor%2A?displayProperty=nameWithType> özelliği kullanın.
  
      - Tüm sürüm dizesi için (örneğin, *4.0.30319.18010*), <xref:System.Version.ToString%2A?displayProperty=nameWithType> yöntemi kullanın. Bu yöntem, kodu yürüten çalışma zamanının sürümünü yansıtan tek bir değer döndürür. Bilgisayara yüklenmiş olan derleme sürümlerini veya diğer çalışma zamanı sürümlerini döndürmez.

  Aşağıdaki örnek, <xref:System.Environment.Version%2A?displayProperty=nameWithType> CLR sürüm bilgilerini almak için özelliği kullanır:
  
  [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
  [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Hangi .NET Framework güncelleştirmelerinin yüklü olduğunu belirleme](how-to-determine-which-net-framework-updates-are-installed.md)
- [Geliştiriciler için .NET Framework'u yükleyin](../install/guide-for-developers.md)
- [.NET Framework sürümleri ve bağımlılıkları](versions-and-dependencies.md)
