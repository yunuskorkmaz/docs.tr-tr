---
title: 'Nasıl yapılır: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme'
ms.date: 02/20/2019
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
ms.openlocfilehash: d7661b3ebaa8f29d6d3b2adbc56c405c8f0945f3
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584180"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Nasıl yapılır: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme

Kullanıcılar yükleyebilir ve kendi bilgisayarlarına .NET Framework'ün birden çok sürümünü çalıştırın. Geliştirme veya uygulamanızı dağıtma, hangi .NET Framework sürümlerinin kullanıcının bilgisayarında yüklü olduğunu bilmeniz gerekebilir. Not: .NET Framework, ayrı ayrı uyarlandı iki ana bileşenden, oluşur  
  
- Koleksiyonları türlerin ve uygulamalarınız için işlevsellik sağlayan kaynaklar derlemelere kümesi. .NET Framework ve derlemeleri, aynı sürüm numarasını paylaşır.  
  
- Yönetir ve uygulamanızın kod yürüten ortak dil çalışma zamanı (CLR). CLR kendi sürüm numarasıyla tanımlanır (bkz [sürümler ve bağımlılıklar](~/docs/framework/migration-guide/versions-and-dependencies.md)).  
  
Bir bilgisayarda yüklü .NET Framework sürümünü doğru bir listesini almak için kayıt defteri görüntüleyebilir veya kod içinde kayıt defterini sorgulayın:  
  
 [.NET Framework sürüm 1-4 kayıt defterinde bulunamadı.](#net_a)  
 [.NET Framework sürüm 4.5 ve sonraki kayıt defterinde Bul)](#net_b)  
 [Kayıt defteri (sürüm 1-4) sorgulamak için kod kullanma](#net_c)  
 [Kayıt defteri (sürüm 4.5 ve üstü) sorgulamak için kod kullanma](#net_d)  
 [Kayıt defteri (sürüm 4.5 ve üstü) sorgulamak için PowerShell'i kullanma](#ps_a)  

 CLR sürümü bulmak için bir aracı veya kodu kullanabilirsiniz:  
  
 [Clrver Aracı'nı kullanma](#clr_a)  
 [System.Environment sınıfı sorgulamak için kod kullanma](#clr_b)  

> [!NOTE]
> .NET Framework sürümünü ve ortak dil çalışma zamanı (CLR) sürümünü arasında bir fark yoktur. .NET Framework sınıf kitaplığı oluşturan derlemeleri kümesine göre .NET Framework sürümü. Örneğin, .NET Framework sürüm 4.5, 4.6.1 ve 4.7.2 içerir. .NET Framework uygulamalarını yürütmek çalışma zamanına göre CLR sürümü tutulan ve tek bir CLR sürümü genellikle birden çok .NET Framework sürümlerini destekler. CLR sürümü 4.30319. *xxxxx* .NET Framework sürüm 4.5.2; aracılığıyla 4 destekler CLR sürümü 4.30319.42000 .NET Framework 4. 6'ile başlayan .NET Framework sürümlerini destekler. Daha fazla bilgi için <xref:System.Environment.Version?displayProperty=nameWithType> özelliği.

 .NET Framework'ün her sürümü için yüklü güncelleştirmeleri algılama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Hangi .NET Framework güncelleştirmelerinin yüklü olduğunu belirleme](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md). .NET Framework'ü yükleme hakkında daha fazla bilgi için bkz: [geliştiriciler için .NET Framework yükleme](../../../docs/framework/install/guide-for-developers.md).  
  
<a name="net_a"></a>   
## <a name="find-net-framework-versions-1-4-in-the-registry"></a>.NET Framework sürüm 1-4 kayıt defterinde bulunamadı. 
  
1.  Üzerinde **Başlat** menüsünde seçin **çalıştırma**.  
  
2.  İçinde **açık** kutusuna **regedit.exe**.  
  
     regedit.exe'yi çalıştırmak için yönetici kimlik bilgileriniz olmalıdır.  
  
3.  Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     .NET Framework sürüm 1.1-3.5 yüklü sürümlerini anahtarlarında olarak listelenen `NDP` alt. Sürüm numarası sürüm alt anahtarında 's depolanan **sürüm** girişi. 
     
     .NET Framework 4 için **sürüm** girdidir altında `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client` alt anahtarı `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full` alt anahtar, veya her iki alt altında.

    > [!NOTE]
    > Kayıt defterindeki "NET Framework Kurulum" klasörü, nokta karakteri ile başlamaz.

    Aşağıdaki şekilde ile birlikte .NET Framework 3.5 için alt gösterir, **sürüm** girişi.

     ![.NET Framework 3.5 için kayıt defteri girişi. ](../../../docs/framework/migration-guide/media/net-4-and-earlier.png ".NET framework 4 ve önceki sürümleri")

<a name="net_b"></a> 
## <a name="find-net-framework-versions-45-and-later-in-the-registry"></a>.NET Framework sürüm 4.5 ve sonraki kayıt defterinde bulun

1. Üzerinde **Başlat** menüsünde seçin **çalıştırma**.

2. İçinde **açık** kutusuna **regedit.exe**.

     regedit.exe'yi çalıştırmak için yönetici kimlik bilgileriniz olmalıdır.

3. Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     Unutmayın yoluna `Full` alt anahtar alt anahtar içerir `Net Framework` yerine `.NET Framework`.

    > [!NOTE]
    > Varsa `Full` alt mevcut değil, ardından .NET Framework 4.5 yok veya sonraki bir sürümü yüklü.

     Adlı bir DWORD değerini denetleyin `Release`. Varlığını `Release` DWORD .NET Framework 4.5 veya sonrası o bilgisayarda yüklü olduğunu gösterir. Değerini belirli bir .NET Framework sürümü için karşılık gelen bir yayın anahtardır. Aşağıdaki şekilde, örneğin değerini `Release` DWORD 378389, .NET Framework 4.5 için yayın anahtar olduğu değeridir. 

     ![.NET Framework 4.5 için kayıt defteri girişi. ](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")

Aşağıdaki tabloda en küçük değerini `Release` DWORD her .NET Framework sürümü için. Bu değerleri şu şekilde kullanabilirsiniz:

- Bir en düşük .NET Framework sürümü mevcut olup olmadığını belirlemek için test olmadığını `Release` DWORD değeri kayıt defterinde bulundu *büyüktür veya eşittir* değeri tabloda listelenen. Örneğin, uygulamanızın gerektirdiği .NET Framework 4.7 ya da daha sonra en düşük sürüm anahtar değeri 460798 için test edersiniz.

- Birden çok sürümü için test etmek için en son .NET Framework sürümü ile başlayın ve ardından her art arda gelen önceki sürümü için test.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|.NET Framework Sürümü|Yayın DWORD değeri|
|--------------------------------|-------------|
|.NET Framework 4.5|378389|
|.NET Framework 4.5.1|378675|
|.NET Framework 4.5.2|379893|
|.NET Framework 4.6|393295|
|.NET Framework 4.6.1|394254|
|.NET Framework 4.6.2|394802|
|.NET framework 4.7|460798|
|.NET framework 4.7.1|461308|
|.NET Framework 4.7.2|461808|

.NET Framework belirli Windows işletim sistemi sürümleri için yayın anahtar tam bir tablo için bkz. [.NET Framework sürüm anahtarları ve Windows işletim sistemi sürümleri](release-keys-and-os-versions.md).

<a name="net_c"></a> 
## <a name="find-net-framework-versions-1-4-with-code"></a>.NET Framework sürüm 1-4 ile kod bulma

- Kullanım <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> sınıfı erişimi `Software\Microsoft\NET Framework Setup\NDP\` alt anahtarı altında `HKEY_LOCAL_MACHINE` Windows kayıt defterinde dal.

     Aşağıdaki kod, bu sorgunun bir örneğini gösterir.

    > [!NOTE]
    > Bu kod, .NET Framework 4.5 veya üzeri algılamak nasıl algılanacağını göstermez. Denetleme `Release` önceki bölümde açıklandığı gibi bu sürümleri algılamak için DWORD. .NET Framework 4.5 veya sonraki sürümler algılayan kod için bu makalenin sonraki bölüme bakın.

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

<a name="net_d"></a> 
## <a name="find-net-framework-versions-45-and-later-with-code"></a>.NET Framework sürüm 4.5 ve sonraki kodu bulun

1. Varlığını `Release` DWORD `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` anahtar, .NET Framework 4.5 veya sonraki bir bilgisayara yüklendiğini belirtir. Anahtar sözcüğü değerini yüklü olan sürümü gösterir. Bu anahtar sözcük denetlemek için kullanmak <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> ve <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> Windows kayıt defteri alt anahtarına erişmek için yöntemleri.

2. Değerini kontrol edin `Release` yüklenen sürümü belirlemek için anahtar sözcüğü. İleri uyumlu olması için tabloda listelenen değerine eşit veya büyük bir değer denetleyebilirsiniz [kayıt defteri bulma .NET Framework sürüm 4.5 ve sonrası](#net_b) bölümü.

Aşağıdaki örnek denetimlerini `Release` .NET Framework 4.5 veya sonraki bir sürümü yüklü olup olmadığını belirlemek için kayıt defteri değeri.

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

Bu örnek, sürüm denetimi için önerilen yöntem aşağıda verilmiştir:

- Denetlediği olup olmadığını değerini `Release` giriş *büyüktür veya eşittir* bilinen yayın anahtarları değeri.

- Eski sürümü için en son sürüm sırayla denetler.

<a name="ps_a"></a> 
## <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a>Bir en düşük gerekli .NET Framework sürüm (4.5 ve üzeri) PowerShell ile denetle

Aşağıdaki örnek değerini denetler `Release` belirlemek için anahtar sözcüğü olup olmadığını .NET Framework 4.6.2 veya üzeri yüklü (döndüren `True` etkinleştirilmişse ve `False` yoksa).

    ```PowerShell
    # PowerShell 5
    Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' | Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
    ```

    ```PowerShell
    # PowerShell 4
    (Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
    ```

    You can replace `394802` in the previous example with another value from the following table in the [Find .NET Framework versions 4.5 and later in the registry](#net_b) section to check for a different minimum required .NET Framework version.
  
<a name="clr_a"></a> 
## <a name="find-the-current-clr-version-with-clrverexe"></a>Clrver.exe geçerli CLR sürümüyle Bul

Bilgisayarda ortak dil çalışma zamanının hangi sürümlerinin yüklü olduğunu saptamak için CLR Sürüm Aracı'nı (Clrver.exe) kullanın.

Visual Studio için geliştirici komut isteminden, girin `clrver`. Bu komut aşağıdakine benzer bir çıktı oluşturur:

```console
Versions installed on the machine:
v2.0.50727
v4.0.30319
```

Bu aracı kullanma hakkında daha fazla bilgi için bkz. [Clrver.exe (CLR sürüm aracı)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).

<a name="clr_b"></a> 
## <a name="find-the-current-clr-version-with-the-environment-class"></a>Geçerli ortam sınıfını CLR sürümüyle Bul

Değerini alabilir <xref:System.Environment.Version?displayProperty=nameWithType> almak için özellik bir <xref:System.Version> şu anda kodu yürüten çalışma zamanının sürümünü tanımlayan nesne. Bu özellik şu anda kodu yürüten çalışma zamanının sürümünü gösteren tek bir değer döndürür; derleme sürümlerini ya da diğer sürümleri bilgisayarda yüklü çalışma zamanı döndürmez. Kullanabileceğiniz <xref:System.Version.Major%2A?displayProperty=nameWithType> (örneğin, "4" sürüm 4.0 için), ana sürüm tanıtıcısını almak için özellik <xref:System.Version.Minor%2A?displayProperty=nameWithType> (örneğin, "0" sürüm 4.0 için), alt sürüm tanıtıcısını almak için özellik veya <xref:System.Version.ToString%2A?displayProperty=nameWithType> tüm sürümü almak için yöntemi dize ("aşağıdaki kodda gösterildiği gibi 4.0.30319.18010"). 

4, 4.5, 4.5.1 ve 4.5.2'yi, .NET Framework sürümleri için <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği döndürür bir <xref:System.Version> nesnenin dize temsili olan form `4.0.30319.xxxxx`. .NET Framework 4.6 ve daha sonra bu biçimde `4.0.30319.42000`.

> [!IMPORTANT]
> .NET Framework 4.5 ve sonrası kullanılması önerilmez <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği çalışma zamanı sürümünü algılayamaz. Bunun yerine, kayıt defteri sorgu açıklandığı öneririz [(.NET Framework 4.5 ve üstü) kod içinde kayıt defterini sorgulayarak .NET Framework sürümlerini bulmak için](#net_d) bu makalenin önceki kısımlarında bölümü.

Aşağıdaki örnekte kullanılan <xref:System.Environment.Version%2A?displayProperty=nameWithType> çalışma zamanı sürüm bilgileri almak için özellik:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Hangi .NET Framework güncelleştirmelerinin yüklü olduğunu belirleme](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)
- [Geliştiriciler için .NET Framework'ü yükleme](../../../docs/framework/install/guide-for-developers.md)
- [Sürümler ve Bağımlılıklar](~/docs/framework/migration-guide/versions-and-dependencies.md)
