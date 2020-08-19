---
title: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme
description: Windows kayıt defterini sorgulayarak bir makineye hangi .NET Framework sürümlerinin yükleneceğini algılamak için kod, regedit.exe veya PowerShell kullanın.
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: 1591aacf5496852609ae571a52aaea2d5c09a15b
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558562"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme

Kullanıcılar bilgisayarlarına .NET Framework birden çok sürümünü [yükleyebilir](../install/index.md) ve çalıştırabilir. Uygulamanızı geliştirirken veya dağıtırken, kullanıcının bilgisayarında hangi .NET Framework sürümlerinin yüklü olduğunu bilmeniz gerekebilir. Kayıt defteri, bir bilgisayarda yüklü .NET Framework sürümlerinin bir listesini içerir.

.NET Framework, sürümü ayrı olan iki ana bileşenden oluşur:

- Uygulamalarınız için işlevsellik sağlayan tür ve kaynak koleksiyonları olan derlemeler kümesi. .NET Framework ve derlemeler aynı sürüm numarasını paylaşır. Örneğin, .NET Framework sürümler 4,5, 4.6.1 ve 4.7.2 ' i içerir.

- Uygulamanızın kodunu yöneten ve yürüten ortak dil çalışma zamanı (CLR). Tek bir CLR sürümü genellikle birden çok .NET Framework sürümü destekler. Örneğin, CLR sürüm 4.0.30319. *xxxxx* , *xxxxx* 42000 ' den az olduğunda, 4 ile 4.5.2 arası sürüm .NET Framework destekler. 4.0.30319.42000 'den büyük veya buna eşit CLR sürümü, .NET Framework 4,6 ' den başlayarak .NET Framework sürümlerini destekler.

Hangi .NET Framework sürümlerinin yüklü olduğunu algılamaya yardımcı olmak için topluluk ile korunan araçlar sunulmaktadır:

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  .NET 2,0 komut satırı aracı.

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  Bir PowerShell 2,0 modülü.

.NET Framework her sürümü için yüklü güncelleştirmeleri algılama hakkında bilgi için bkz. [nasıl yapılır: hangi .NET Framework güncelleştirmelerinin yükleneceğini belirleme](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="detect-net-framework-45-and-later-versions"></a>.NET Framework 4,5 ve sonraki sürümleri Algıla

Bir makinede yüklü .NET Framework (4,5 ve üzeri) sürümü, **HKEY_LOCAL_MACHINE \\ yazılım \\ Microsoft \\ net Framework Setup \\ NDP \\ v4 \\ Full**bölümünde kayıt defterinde listelenmiştir. **Tam** alt anahtar eksikse, .NET Framework 4,5 veya üzeri yüklü değildir.

> [!NOTE]
> Kayıt defteri yolundaki **net Framework kurulum** alt anahtarı bir noktayla *başlamaz.*

Kayıt defterindeki **Release** REG_DWORD değeri, yüklü .NET Framework sürümünü temsil eder.

<a name="version_table"></a>

| .NET Framework sürümü | **Yayın** değeri |
| ---------------------- | -------------------------- |
| .NET Framework 4.5     | Tüm Windows işletim sistemleri: 378389 |
| .NET Framework 4.5.1   | Windows 8.1 ve Windows Server 2012 R2 'de: 378675<br />Diğer tüm Windows işletim sistemlerinde: 378758 |
| .NET Framework 4.5.2   | Tüm Windows işletim sistemleri: 379893 |
| .NET Framework 4.6     | Windows 10:393295 ' de<br />Diğer tüm Windows işletim sistemlerinde: 393297 |
| .NET Framework 4.6.1   | Windows 10 Kasım güncelleştirme sistemlerinde: 394254<br />Diğer tüm Windows işletim sistemlerinde (Windows 10 dahil): 394271 |
| .NET Framework 4.6.2   | Windows 10 yıldönümü güncelleştirmesi ve Windows Server 2016:394802<br />Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 394806 |
|  .NET Framework 4.7     | Windows 10 Creators Update üzerinde: 460798<br />Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 460805 |
| .NET Framework 4.7.1   | Windows 10 Fall Creators Update ve Windows Server, sürüm 1709:461308<br/>Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 461310 |
|  .NET Framework 4.7.2   | Windows 10 Nisan 2018 güncelleştirmesi ve Windows Server, sürüm 1803:461808<br/>Windows 10 Nisan 2018 güncelleştirmesi ve Windows Server, sürüm 1803 dışındaki tüm Windows işletim sistemlerinde: 461814 |
|  .NET Framework 4.8     | Windows 10 Mayıs 2019 güncelleştirmesi ve Windows 10 Kasım 2019 güncelleştirmesi: 528040<br/>Windows 10 Mayıs 2020 güncelleştirmesi: 528372<br/>Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 528049 |

### <a name="minimum-version"></a>En düşük sürüm

.NET Framework *En düşük* sürümünün mevcut olup olmadığını anlamak için önceki tablodan bu sürüm için en küçük **Sürüm** REG_DWORD değerini kullanın.

Örneğin, uygulamanız .NET Framework 4,8 veya sonraki bir sürümde çalışıyorsa, 528040 ' *den büyük veya buna eşit* olan bir **yayın** REG_DWORD değeri için test edin.

| .NET Framework sürümü | En küçük değer |
| ---------------------- | ------------- |
| .NET Framework 4.5     | 378389 |
| .NET Framework 4.5.1   | 378675 |
| .NET Framework 4.5.2   | 379893 |
| .NET Framework 4.6     | 393295 |
| .NET Framework 4.6.1   | 394254 |
| .NET Framework 4.6.2   | 394802 |
|  .NET Framework 4.7     | 460798 |
| .NET Framework 4.7.1   | 461308 |
|  .NET Framework 4.7.2   | 461808 |
|  .NET Framework 4.8     | 528040 |

### <a name="use-registry-editor"></a>Kayıt Defteri Düzenleyicisi 'Ni kullan

01. **Başlat** menüsünde, **Çalıştır**' ı seçin, *Regedit*' i girin ve **Tamam**' ı seçin.

    Regedit 'i çalıştırmak için yönetici kimlik bilgilerine sahip olmanız gerekir.

01. Kayıt Defteri Düzenleyicisi 'nde, aşağıdaki alt anahtarı açın: ** \\ yazılım \\ Microsoft \\ net Framework Setup \\ NDP \\ v4 \\ Full HKEY_LOCAL_MACHINE**. **Tam** alt anahtar yoksa, .NET Framework 4,5 veya sonraki bir sürümü yüklü değildir.

01. **Yayın**adlı REG_DWORD girişi olup olmadığını denetleyin. Varsa, .NET Framework 4,5 veya sonraki bir sürümü yüklemiş olursunuz. Değeri, .NET Framework belirli bir sürümüne karşılık gelir. Aşağıdaki şekilde, örneğin, **Sürüm** girişinin değeri 528040 ' dir. bu, .NET Framework 4,8 ' in sürüm anahtarıdır.

    ![.NET Framework 4,5 için kayıt defteri girişi](./media/clr-installdir.png ".NET Framework 4,5 için kayıt defteri girişi")

### <a name="use-powershell-to-check-for-a-minimum-version"></a>En düşük sürümü denetlemek için PowerShell 'i kullanma

PowerShell komutlarını, **HKEY_LOCAL_MACHINE \\ yazılım \\ Microsoft \\ net Framework Setup \\ NDP \\ v4 \\ Full** alt anahtarının **yayın** girişinin değerini denetlemek için kullanın.

Aşağıdaki örnekler, .NET Framework 4.6.2 veya sonraki bir sürümün yüklenip yüklenmediğini anlamak için **yayın** girişinin değerini denetler. Bu kod `True` , yüklenmişse ve `False` Aksi takdirde döndürülür.

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a>Kodu kullanarak kayıt defterini sorgulama

01. <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> Windows kayıt defterindeki **HKEY_LOCAL_MACHINE \\ Software \\ Microsoft \\ net Framework Setup \\ NDP \\ v4 \\ Full** alt anahtarına erişmek için ve yöntemlerini kullanın.

    > [!IMPORTANT]
    > Çalıştırdığınız uygulama 32-bit ise ve 64 bit Windows 'da çalışıyorsa, kayıt defteri yolları daha önce listelenenden farklı olacaktır. 64 bit kayıt defteri **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\ ** alt anahtarında kullanılabilir. Örneğin, .NET Framework 4,5 için kayıt defteri alt anahtarı **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\ Microsoft \\ net Framework Setup \\ NDP \\ v4 \\ Full**' dır.

01. Yüklü sürümü öğrenmek için **yayın** REG_DWORD değerini denetleyin. İleriye dönük olarak uyumlu olması için [.NET Framework sürüm tablosunda](#version_table)listelenen değerden daha büyük veya ona eşit bir değer olup olmadığını kontrol edin.

Aşağıdaki örnek, yüklü olan .NET Framework 4,5 ve sonraki sürümlerini bulmak için kayıt defterindeki **yayın** girişinin değerini denetler:

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

Bu örnek sürüm denetimi için önerilen yöntemi izler:

- **Yayın** girişi değerinin bilinen yayın anahtarlarının değerinden *büyük veya* bu değere eşit olup olmadığını denetler.
- En son sürümden en eski sürüme sırayla kontrol eder.

## <a name="detect-net-framework-10-through-40"></a>1,0 ile 4,0 arasındaki .NET Framework Algıla

1,1 ' den 4,0 ' e .NET Framework her sürümü **HKEY_LOCAL_MACHINE \\ Software \\ Microsoft \\ net Framework Setup \\ NDP**alt anahtarı olarak listelenmiştir. Aşağıdaki tabloda her bir .NET Framework sürümünün yolu listelenmektedir. Çoğu sürüm için, **Install** `1` Bu sürümün yüklü olduğunu göstermek için bir Install REG_DWORD değeri vardır. Bu alt anahtarlarda, sürüm dizesi içeren bir **sürüm** REG_SZ değeri de vardır.

> [!NOTE]
> Kayıt defteri yolundaki **net Framework kurulum** alt anahtarı bir noktayla *başlamaz.*

| Framework sürümü  | Kayıt defteri alt anahtarı | Değer |
| ------------------ | --------------- | ----- |
| 1,0                | **HKLM \\ Software \\ Microsoft \\ . NETFramework \\ ilkesi \\ v 1.0 \\ 3705**     | **Yüklemesi** REG_SZ eşittir `1` |
| 1.1                | **HKLM \\ Software \\ Microsoft \\ net Framework Setup \\ NDP \\ v 1.1.4322**   | **Yüklemesi** REG_DWORD eşittir `1` |
| 2,0                | **HKLM \\ Software \\ Microsoft \\ net Framework Setup \\ NDP \\ v 2.0.50727**  | **Yüklemesi** REG_DWORD eşittir `1` |
| 3,0                | **HKLM \\ Software \\ Microsoft \\ net Framework Setup \\ NDP \\ v 3.0 \\ kurulumu** | **Installsuccess** REG_DWORD eşittir `1` |
| 3,5                | **HKLM \\ Software \\ Microsoft \\ net Framework Setup \\ NDP \\ v 3.5**        | **Yüklemesi** REG_DWORD eşittir `1` |
| 4,0 istemci profili | **HKLM \\ Software \\ Microsoft \\ net Framework Setup \\ NDP \\ v4 \\ istemcisi**  | **Yüklemesi** REG_DWORD eşittir `1` |
| 4,0 tam profil   | **HKLM \\ Software \\ Microsoft \\ net Framework Kurulumu \\ NDP \\ v4 \\ dolu**    | **Yüklemesi** REG_DWORD eşittir `1` |

> [!IMPORTANT]
> Çalıştırdığınız uygulama 32-bit ise ve 64 bit Windows 'da çalışıyorsa, kayıt defteri yolları daha önce listelenenden farklı olacaktır. 64 bit kayıt defteri **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\ ** alt anahtarında kullanılabilir. Örneğin, .NET Framework 3,5 için kayıt defteri alt anahtarı **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\ Microsoft \\ net Framework Setup \\ NDP \\ v 3.5**' dir.

.NET Framework 1,0 alt anahtarına yönelik kayıt defteri yolunun diğerlerinden farklı olduğunu unutmayın.

### <a name="use-registry-editor-older-framework-versions"></a>Kayıt Defteri Düzenleyicisi 'Ni kullan (eski Framework sürümleri)

01. **Başlat** menüsünde, **Çalıştır**' ı seçin, *Regedit*' i girin ve **Tamam**' ı seçin.

    Regedit 'i çalıştırmak için yönetici kimlik bilgilerine sahip olmanız gerekir.

01. Denetlemek istediğiniz sürümle eşleşen alt anahtarı açın. [.NET Framework 1,0 ile 4,0 arasında algılama](#detect-net-framework-10-through-40) bölümünde bulunan tabloyu kullanın.

    Aşağıdaki şekilde, .NET Framework 3,5 için alt anahtar ve **Sürüm** değeri gösterilmektedir.

    ![3,5 .NET Framework için kayıt defteri girişi.](./media/net-4-and-earlier.png ".NET Framework 3,5 ve önceki sürümler")

### <a name="query-the-registry-using-code-older-framework-versions"></a>Kodu kullanarak kayıt defterini sorgulama (eski Framework sürümleri)

<xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType>Windows kayıt defterindeki **HKEY_LOCAL_MACHINE \\ Software \\ Microsoft \\ net Framework Setup \\ NDP** alt anahtarına erişmek için sınıfını kullanın.

> [!IMPORTANT]
> Çalıştırdığınız uygulama 32-bit ise ve 64 bit Windows 'da çalışıyorsa, kayıt defteri yolları daha önce listelenenden farklı olacaktır. 64 bit kayıt defteri **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\ ** alt anahtarında kullanılabilir. Örneğin, .NET Framework 3,5 için kayıt defteri alt anahtarı **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\ Microsoft \\ net Framework Setup \\ NDP \\ v 3.5**' dir.

Aşağıdaki örnek, yüklü .NET Framework 1 ila 4 sürümü bulur:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a>CLR sürümlerini bul

.NET Framework ile yüklenen .NET Framework CLR 'nin sürümü ayrı olarak sağlanır. .NET Framework CLR sürümünü algılamamanın iki yolu vardır:

- **Clrver.exe aracı**

  Clr [Sürüm aracı 'nı (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) kullanarak bir bılgısayarda hangi CLR sürümlerinin yüklü olduğunu saptayın. [Visual Studio için geliştirici komut istemi](../tools/developer-command-prompt-for-vs.md) açın ve girin `clrver` .

  Örnek çıktı:

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- **`Environment`Sınıfı**

  > [!IMPORTANT]
  > .NET Framework 4,5 ve sonraki sürümlerinde, <xref:System.Environment.Version%2A?displayProperty=nameWithType> CLR sürümünü algılamak için özelliğini kullanmayın. Bunun yerine, kayıt defterini [.NET Framework 4,5 ve sonraki sürümlerinde](#detect-net-framework-45-and-later-versions)açıklandığı gibi sorgulayın.
  
  01. <xref:System.Environment.Version?displayProperty=nameWithType>Nesneyi almak için özelliği sorgulayın <xref:System.Version> .
  
      Döndürülen `System.Version` nesne, şu anda kodu yürüten çalışma zamanının sürümünü tanımlar. Derleme sürümlerini veya çalışma zamanının bilgisayarda yüklü olabilecek diğer sürümlerini döndürmez.
  
      .NET Framework sürümleri 4, 4,5, 4.5.1 ve 4.5.2 için, döndürülen nesnenin dize temsili <xref:System.Version> 4.0.30319 biçimindedir.* xxxxx*, *xxxxx* 42000 ' den küçük. .NET Framework 4,6 ve sonraki sürümlerinde, 4.0.30319.42000 biçiminde olur.
  
  01. **Sürüm** nesnesine sahip olduktan sonra, aşağıdaki gibi sorgulayın:
  
      - Ana yayın tanımlayıcısı için (örneğin, sürüm 4,0 için *4* ), <xref:System.Version.Major%2A?displayProperty=nameWithType> özelliğini kullanın.
  
      - Küçük yayın tanımlayıcısı için (örneğin, sürüm 4,0 için *0* ), <xref:System.Version.Minor%2A?displayProperty=nameWithType> özelliğini kullanın.
  
      - Tüm sürüm dizesi için (örneğin, *4.0.30319.18010*), <xref:System.Version.ToString%2A?displayProperty=nameWithType> yöntemini kullanın. Bu yöntem, kodu yürüten çalışma zamanının sürümünü yansıtan tek bir değer döndürür. Bu, bilgisayarda yüklü olabilecek derleme sürümlerini veya diğer çalışma zamanı sürümlerini döndürmez.

  Aşağıdaki örnek <xref:System.Environment.Version%2A?displayProperty=nameWithType> CLR sürüm bilgilerini almak için özelliğini kullanır:
  
  [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
  [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: hangi .NET Framework güncelleştirmelerinin yükleneceğini belirleme](how-to-determine-which-net-framework-updates-are-installed.md)
- [Geliştiriciler için .NET Framework yüklemesi](../install/guide-for-developers.md)
- [.NET Framework sürümleri ve bağımlılıklar](versions-and-dependencies.md)
