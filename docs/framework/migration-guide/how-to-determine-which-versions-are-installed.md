---
title: 'Nasıl yapılır: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme'
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e6086772b807440570b94cfff268aa1d78fa048
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490009"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Nasıl yapılır: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme

Kullanıcılar [yükleme](https://docs.microsoft.com/dotnet/framework/install) ve .NET Framework'ün birden çok sürümü bilgisayarlarında çalıştırır. Geliştirme veya uygulamanızı dağıtma, hangi .NET Framework sürümlerinin kullanıcının bilgisayarında yüklü olduğunu bilmeniz gerekebilir.

.NET Framework, ayrı ayrı uyarlandı iki ana bileşenden, oluşur:

- Koleksiyonları türlerin ve uygulamalarınız için işlevsellik sağlayan kaynaklar derlemelere kümesi. .NET Framework ve derlemeleri, aynı sürüm numarasını paylaşır.

- Yönetir ve uygulamanızın kod yürüten ortak dil çalışma zamanı (CLR). CLR kendi sürüm numarasıyla tanımlanır (bkz [sürümler ve bağımlılıklar](~/docs/framework/migration-guide/versions-and-dependencies.md)).

> [!NOTE]
> .NET Framework'ün her yeni sürümü önceki sürümlerdeki özellikleri korur ve yeni özellikler ekler. Önceki sürümleri kaldırmadan .NET Framework yükleme, yani aynı anda tek bir bilgisayara .NET Framework'ün birden çok sürümü yükleyebilirsiniz. Genel olarak, bir uygulama belirli bir sürüme bağlı olabileceği veya o sürüm kaldırılırsa bozulabileceği için .NET Framework'ün önceki sürümlerini kaldırın olmamalıdır.
>
> .NET Framework sürümü ve CLR sürümü arasında bir fark vardır:
> - .NET Framework sürümü .NET Framework sınıf kitaplığı oluşturan derlemeleri kümesini temel alır. Örneğin, .NET Framework sürüm 4.5, 4.6.1 ve 4.7.2 içerir.
>- CLR sürümü, .NET Framework uygulamaları, üzerinde yürütme çalışma zamanı temel alır. Tek bir CLR sürümü, genellikle birden çok .NET Framework sürümlerini destekler. Örneğin, CLR sürüm 4.0.30319. *xxxxx* .NET Framework sürüm 4.5.2, 4 destekler burada *xxxxx* küçüktür 42000 olduğunu ve CLR sürümü 4.0.30319.42000 .NET Framework 4. 6'ile başlayan .NET Framework sürümlerini destekler.
>
> Sürümleri hakkında daha fazla bilgi için bkz. [.NET Framework sürümleri ve bağımlılıkları](versions-and-dependencies.md).

Bir bilgisayarda yüklü .NET Framework sürümlerinin bir listesini almak için kayıt defterine erişim. Kayıt defterini veya kodu sorgulamanız için bunu kullanın ya da Kayıt Defteri Düzenleyicisi'ni kullanabilirsiniz:

- Yeni bir .NET Framework sürümleri (4.5 ve üzeri) bulun:
  - [.NET Framework sürümlerini bulmak için Kayıt Defteri Düzenleyicisi'ni kullanın](#net_b)
  - [.NET Framework sürümleri için kayıt defterini sorgulayın için kodu kullanın](#net_d)
  - [.NET Framework sürümleri için kayıt defterini sorgulayın için PowerShell kullanma](#ps_a)
- Eski .NET Framework sürümlerini bulmak (1&#8211;4):
  - [.NET Framework sürümlerini bulmak için Kayıt Defteri Düzenleyicisi'ni kullanın](#net_a)
  - [.NET Framework sürümleri için kayıt defterini sorgulayın için kodu kullanın](#net_c)

Bir bilgisayarda yüklü CLR sürümlerin listesini almak için bir aracı veya kod kullanın:

- [Clrver aracını kullanma](#clr_a)
- [Ortam sınıfını sorgulamak için kodu kullanın.](#clr_b)

.NET Framework'ün her sürümü için yüklü güncelleştirmeleri algılama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Hangi .NET Framework güncelleştirmelerinin yüklü olduğunu belirleme](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="find-newer-net-framework-versions-45-and-later"></a>(4.5 ve üzeri) daha yeni .NET Framework sürümlerini bulmak

<a name="net_b"></a>

### <a name="find-net-framework-versions-45-and-later-in-the-registry"></a>.NET Framework sürüm 4.5 ve sonraki kayıt defterinde bulun

1. Gelen **Başlat** menüsünde seçin **çalıştırma**, girin *regedit*ve ardından **Tamam**.

     Regedit çalıştırmak için yönetici kimlik bilgileriniz olmalıdır.

2. Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın: **Hkey_local_machıne\software\microsoft\net Framework Setup\NDP\v4\Full**. Varsa **tam** alt hazır değilse, ardından .NET Framework 4.5 yoksa veya sonraki bir sürümü yüklü.

    > [!NOTE]
    > **NET Framework Kurulum** klasörünü mu *değil* bir noktayla başlar.

3. Adlı bir DWORD girişini denetleyin **yayın**. Varsa, ardından, .NET Framework 4.5 veya sonraki bir sürümünün yüklü olması. Değerini belirli bir .NET Framework sürümüne karşılık gelen bir yayın anahtardır. Aşağıdaki şekilde, örneğin değerini **yayın** girdidir *378389*, .NET Framework 4.5 için yayın anahtar olduğu.

     ![.NET Framework 4.5 için kayıt defteri girişi](media/clr-installdir.png ".NET Framework 4.5 için kayıt defteri girişi")

Değeri aşağıdaki tabloda **yayın** DWORD tek işletim sistemlerinde .NET Framework 4.5 ve sonraki sürümler için.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|.NET Framework sürümü|Yayın DWORD değeri|
|--------------------------------|-------------|
|.NET Framework 4.5|Tüm Windows işletim sistemleri: 378389|
|.NET Framework 4.5.1|Windows 8.1 ve Windows Server 2012 R2 üzerinde: 378675<br />Diğer Windows üzerinde işletim sistemleri: 378758|
|.NET Framework 4.5.2|Tüm Windows işletim sistemleri: 379893|
|.NET Framework 4.6|Windows 10: 393295<br />Diğer Windows üzerinde işletim sistemleri: 393297|
|.NET Framework 4.6.1|Windows 10 Kasım güncelleştirmesi sistemlerinde: 394254<br />Diğer Windows üzerinde işletim sistemleri (Windows 10 dahil): 394271|
|.NET Framework 4.6.2|Windows 10 Yıldönümü güncelleştirmesi ve Windows Server 2016 üzerinde: 394802<br />Diğer Windows üzerinde işletim sistemleri (dahil diğer Windows 10 işletim sistemleri): 394806|
|.NET framework 4.7|Üzerinde Windows 10 Creators güncelleştirmesi: 460798<br />Diğer Windows üzerinde işletim sistemleri (dahil diğer Windows 10 işletim sistemleri): 460805|
|.NET framework 4.7.1|Windows 10 Fall Creators Update ve Windows Server 1709 sürümü: 461308<br/>Diğer Windows üzerinde işletim sistemleri (dahil diğer Windows 10 işletim sistemleri): 461310|
|.NET Framework 4.7.2|Windows 10 Nisan 2018 güncelleştirmesi ve Windows Server, 1803 sürüm: 461808<br/>Windows 10 Nisan 2018 dışındaki tüm Windows işletim sistemlerinde güncelleştirmesi ve Windows Server, 1803 sürüm: 461814|
|.NET Framework 4.8|Windows 10 Mayıs 2019 güncelleştirmesinde: 528040<br/>Diğer tüm üzerinde Windows işletim sistemleri (dahil diğer Windows 10 işletim sistemleri): 528049|

Bu değerleri şu şekilde kullanabilirsiniz:

- Belirli bir Windows işletim sistemi sürümü, .NET Framework'ün belirli bir sürümü yüklü olup olmadığını belirlemek için test olmadığını **yayın** DWORD değeri *eşit* listelenen değeri Tablo. Örneğin, .NET Framework 4.6 bir Windows 10 sistemde mevcut olup olmadığını belirlemek için test bir **yayın** değeri olan *eşit* 393295.

- .NET Framework'ün en düşük bir sürüm mevcut olup olmadığını belirlemek için küçük kullanın **yayın** DWORD değeri bu sürümü için. Uygulamanız .NET Framework 4.6 veya sonraki bir sürümü altında çalışıyorsa, örneğin, test bir **yayın** DWORD değeri *büyüktür veya eşittir* 393295. Yalnızca en düşük listeleyen bir tablo için **yayın** her .NET Framework sürümü için DWORD değerini görmek [en düşük .NET Framework 4.5 ve sonraki sürümleri için yayın DWORD değerlerini](minimum-release-dword.md).

- Birden çok sürümü için test etmek için bir değer için test ederek başlamak *büyüktür veya eşittir* daha küçük bir DWORD değeri için en son .NET Framework sürümü ve her biri için değer daha küçük bir DWORD değeri ile karşılaştırmak art arda gelen önceki sürümü. İçin test ederek uygulamanızın gerektirdiği .NET Framework 4.7 veya üzeri ve mevcut .NET Framework'ün belirli sürümü belirlemek istiyorsanız, örneğin, başlangıç bir **yayın** DWORD değeri *değerinden büyük veya eşittir*  461808 (.NET Framework 4.7.2 için daha küçük DWORD değerini) için. Ardından karşılaştırma **yayın** DWORD değerini daha sonra her .NET Framework sürümü için daha küçük değerine sahip. Yalnızca en düşük listeleyen bir tablo için **yayın** her .NET Framework sürümü için DWORD değerini görmek [en düşük .NET Framework 4.5 ve sonraki sürümleri için yayın DWORD değerlerini](minimum-release-dword.md).

<a name="net_d"></a>

### <a name="find-net-framework-versions-45-and-later-with-code"></a>.NET Framework sürüm 4.5 ve sonraki kodu bulun

1. Kullanım <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> ve <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> erişmek için yöntemleri **hkey_local_machıne\software\microsoft\net Framework Setup\NDP\v4\Full** Windows kayıt defteri alt anahtarı.

    Varlığını **yayın** DWORD girişte **hkey_local_machıne\software\microsoft\net Framework Setup\NDP\v4\Full** alt anahtar, .NET Framework 4.5 veya sonraki bir sürümü olduğunu gösterir bir bilgisayarda yüklü.

2. Değerini kontrol edin **yayın** yüklenen sürümü belirlemek için giriş. İleri uyumlu olacak şekilde, daha büyük bir değer olup olmadığını denetleyin veya listelenen değerine eşit [.NET Framework sürüm tablosu](#version_table).

Aşağıdaki örnek değeri kontrol **yayın** yüklü olan sonraki sürümleri ve .NET Framework 4.5 bulmak için kayıt defteri girişi:

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

Bu örnek, sürüm denetimi için önerilen yöntem aşağıda verilmiştir:

- Denetler olup olmadığını değerini **yayın** girdidir *büyüktür veya eşittir* bilinen yayın anahtar değeri.

- Eski sürümü için en son sürüm sırayla denetler.

<a name="ps_a"></a>

### <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a>Gereken en düşük .NET Framework sürümünü (4.5 ve üzeri) PowerShell ile denetle

- Değerini denetlemek için PowerShell komutlarını kullanın **yayın** girişi **hkey_local_machıne\software\microsoft\net Framework Setup\NDP\v4\Full** alt.

Aşağıdaki örnekler değerini kontrol edin **yayın** belirlemek için giriş olmadığını .NET Framework 4.6.2 veya üzeri yüklü. Bu kodu döndürür `True` yüklüyse ve `False` Aksi takdirde.

```PowerShell
# PowerShell 5
 Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' |  Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 }
 ```

```PowerShell
# PowerShell 4
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

Bir farklı gereken en düşük .NET Framework sürümü için denetlenecek değiştirin *394802* ile bu örneklerde bir **yayın** değerini [.NET Framework sürüm tablosu](#version_table).

## <a name="find-older-net-framework-versions-182114"></a>Eski .NET Framework sürümlerini bulmak (1&#8211;4)

<a name="net_a"></a>

### <a name="find-net-framework-versions-182114-in-the-registry"></a>.NET Framework sürümlerini 1 bulmak&#8211;4'te kayıt defteri

1. Gelen **Başlat** menüsünde seçin **çalıştırma**, girin *regedit*ve ardından **Tamam**.

    Regedit çalıştırmak için yönetici kimlik bilgileriniz olmalıdır.

2. Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın: **Hkey_local_machıne\software\microsoft\net Framework Setup\NDP**:

    - .NET Framework sürüm 3.5 ile 1.1 yüklü her sürüm alt anahtarı altında listelenir **hkey_local_machıne\software\microsoft\net Framework Setup\NDP** alt. Örneğin, **hkey_local_machıne\software\microsoft\net Framework Setup\NDP\v3.5**. Sürüm numarasını sürümü alt anahtarının değeri olarak depolanan **sürüm** girişi.

    - .NET Framework 4 için **sürüm** girdidir altında **hkey_local_machıne\software\microsoft\net Framework Setup\NDP\v4.0\Client** alt anahtarı **HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\NET Framework Setup\NDP\v4.0\Full** alt anahtar, veya her iki alt altında.

    > [!NOTE]
    > **NET Framework Kurulum** klasörünü noktayla başlayan değil.

    Alt aşağıdaki şekilde gösterilmiştir ve kendi **sürüm** .NET Framework 3.5 için giriş.

    ![.NET Framework 3.5 için kayıt defteri girişi. ](media/net-4-and-earlier.png ".NET framework 3.5 ve önceki sürümleri")

<a name="net_c"></a>

### <a name="find-net-framework-versions-182114-with-code"></a>.NET Framework sürümlerini 1 bulmak&#8211;kodla 4

- Kullanım <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> sınıfı erişimi **hkey_local_machıne\software\microsoft\net Framework Setup\NDP** Windows kayıt defteri alt anahtarı.

Aşağıdaki örnek, .NET Framework 1 bulur&#8211;yüklü olan 4 sürümleri:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a>CLR sürümleri bulun

<a name="clr_a"></a>

### <a name="find-the-current-clr-version-with-clrverexe"></a>Clrver.exe geçerli CLR sürümüyle Bul

Kullanım [CLR sürüm Aracı (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) CLR'ın hangi sürümleri bir bilgisayarda yüklü olduğunu saptamak için:

- Gelen bir [Visual Studio için geliştirici komut istemi](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs), girin `clrver`.

    Örnek çıktı:

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a>

### <a name="find-the-current-clr-version-with-the-environment-class"></a>Geçerli ortam sınıfını CLR sürümüyle Bul

> [!IMPORTANT]
> .NET Framework 4.5 ve sonraki sürümler için kullanmadığınız <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği CLR sürümünü algılayamaz. Bunun yerine, açıklanan şekilde kayıt defterini sorgulayın [Bul .NET Framework sürüm 4.5 ve sonraki kod ile](#net_d).

1. Sorgu <xref:System.Environment.Version?displayProperty=nameWithType> almak için özellik bir <xref:System.Version> nesne.

    Döndürülen `System.Version` nesne şu anda kodu yürüten çalışma zamanının sürümünü tanımlar. Derleme sürümlerini ya da diğer sürümleri bilgisayarda yüklü çalışma zamanı döndürmüyor.

    .NET Framework sürüm 4, 4.5, 4.5.1 ve 4.5.2'yi, döndürülen dize gösterimi için <xref:System.Version> nenesindeki formun 4.0.30319. *xxxxx*burada *xxxxx* küçüktür 42000 olduğu. .NET Framework 4.6 ve sonraki sürümler için formun 4.0.30319.42000 sahiptir.

2. Sonra `Version` nesne, şu şekilde sorgulayın:

   - Tanımlayıcı için ana sürüm (örneğin, *4* sürüm 4.0 için), kullanın <xref:System.Version.Major%2A?displayProperty=nameWithType> özelliği.

   - Tanımlayıcı için ikincil sürüm (örneğin, *0* sürüm 4.0 için), kullanın <xref:System.Version.Minor%2A?displayProperty=nameWithType> özelliği.

   - İçin tüm sürüm dizesini (örneğin, *4.0.30319.18010*), kullanın <xref:System.Version.ToString%2A?displayProperty=nameWithType> yöntemi. Bu yöntem, kodu yürüten çalışma zamanının sürümünü gösteren tek bir değer döndürür. Derleme sürümlerini veya bilgisayarda yüklü diğer çalışma zamanı sürümleri döndürmez.

Aşağıdaki örnekte <xref:System.Environment.Version%2A?displayProperty=nameWithType> CLR sürümü bilgisini almak için özellik:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Hangi .NET Framework güncelleştirmelerinin yüklü olduğunu belirleme](how-to-determine-which-net-framework-updates-are-installed.md)
- [Geliştiriciler için .NET Framework'ü yükleme](../install/guide-for-developers.md)
- [.NET framework sürümleri ve bağımlılıkları](versions-and-dependencies.md)
