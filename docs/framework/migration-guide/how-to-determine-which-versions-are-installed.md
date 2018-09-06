---
title: 'Nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme'
ms.date: 04/10/2018
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
ms.openlocfilehash: 1874d5512f04f22b9c53bdc9e92d0c96e45d21c8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43787084"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme

Kullanıcılar yükleyebilir ve kendi bilgisayarlarına .NET Framework'ün birden çok sürümünü çalıştırın. Geliştirme veya uygulamanızı dağıtma, hangi .NET Framework sürümlerinin kullanıcının bilgisayarında yüklü olduğunu bilmeniz gerekebilir. Not: .NET Framework, ayrı ayrı uyarlandı iki ana bileşenden, oluşur  
  
-   Koleksiyonları türlerin ve uygulamalarınız için işlevsellik sağlayan kaynaklar derlemelere kümesi. .NET Framework ve derlemeleri, aynı sürüm numarasını paylaşır.  
  
-   Yönetir ve uygulamanızın kod yürüten ortak dil çalışma zamanı (CLR). CLR kendi sürüm numarasıyla tanımlanır (bkz [sürümler ve bağımlılıklar](~/docs/framework/migration-guide/versions-and-dependencies.md)).  
  
 Bir bilgisayarda yüklü .NET Framework sürümünü doğru bir listesini almak için kayıt defteri görüntüleyebilir veya kod içinde kayıt defterini sorgulayın:  
  
 [Kayıt defteri (sürüm 1-4) görüntüleme](#net_a)  
 [Kayıt defteri (sürüm 4.5 ve üstü) görüntüleme](#net_b)  
 [Kayıt defteri (sürüm 1-4) sorgulamak için kod kullanma](#net_c)  
 [Kayıt defteri (sürüm 4.5 ve üstü) sorgulamak için kod kullanma](#net_d)  
 [Kayıt defteri (sürüm 4.5 ve üstü) sorgulamak için PowerShell'i kullanma](#ps_a)  
  
 CLR sürümü bulmak için bir aracı veya kodu kullanabilirsiniz:  
  
 [Clrver Aracı'nı kullanma](#clr_a)  
 [System.Environment sınıfı sorgulamak için kod kullanma](#clr_b)  
  
 .NET Framework'ün her sürümü için yüklü güncelleştirmeleri algılama hakkında daha fazla bilgi için bkz: [nasıl yapılır: belirlemek, .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md). .NET Framework'ü yükleme hakkında daha fazla bilgi için bkz: [geliştiriciler için .NET Framework yükleme](../../../docs/framework/install/guide-for-developers.md).  
  
<a name="net_a"></a>   
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a>Kayıt defteri (.NET Framework 1-4) görüntüleyerek .NET Framework sürümlerini bulmak için  
  
1.  Üzerinde **Başlat** menüsünde seçin **çalıştırma**.  
  
2.  İçinde **açık** kutusuna **regedit.exe**.  
  
     regedit.exe'yi çalıştırmak için yönetici kimlik bilgileriniz olmalıdır.  
  
3.  Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     Yüklenen sürümler NDP alt anahtarı altında listelenir. Sürüm numarasını depolanan **sürüm** girişi. İçin [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] **sürüm** girdidir istemci veya tam alt anahtarın (NDP'nin), altında veya her iki alt altında.  
  

    > [!NOTE]
    > Kayıt defterindeki "NET Framework Kurulum" klasörü, nokta karakteri ile başlamaz.

<a name="net_b"></a> 
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a>Kayıt defteri (.NET Framework 4.5 ve üstü) görüntüleyerek .NET Framework sürümlerini bulmak için

1. Üzerinde **Başlat** menüsünde seçin **çalıştırma**.

2. İçinde **açık** kutusuna **regedit.exe**.

     regedit.exe'yi çalıştırmak için yönetici kimlik bilgileriniz olmalıdır.

3. Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     Unutmayın yoluna `Full` alt anahtar alt anahtar içerir `Net Framework` yerine `.NET Framework`.

    > [!NOTE]
    > Varsa `Full` alt mevcut değil, ardından .NET Framework 4.5 yok veya sonraki bir sürümü yüklü.

     Adlı bir DWORD değerini denetleyin `Release`. Varlığını `Release` DWORD gösterir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ya da daha yeni bu bilgisayarda yüklü.

     ![.NET Framework 4.5 için kayıt defteri girişi. ](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")

     Değerini `Release` DWORD hangi .NET Framework sürümünün yüklü olduğunu gösterir.

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |Yayın DWORD değeri|Sürüm|
    |--------------------------------|-------------|
    |378389|.NET Framework 4.5|
    |378675|.NET framework 4.5.1 Windows 8.1 veya Windows Server 2012 R2 ile yüklenen|
    |378758|.NET framework 4.5.1 Windows 8, Windows 7 SP1 veya Windows Vista SP2 yüklü|
    |379893|.NET Framework 4.5.2|
    |Yalnızca Windows 10 sistemlerinde: 393295<br /><br /> Diğer tüm işletim sistemi sürümlerinde: 393297|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |Yalnızca Windows 10 Kasım güncelleştirmesi sistemlerinde: 394254<br /><br /> Diğer tüm işletim sistemi sürümlerinde: 394271|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |Windows 10 Yıldönümü güncelleştirmesi ve Windows Server 2016:394802<br /><br /> Diğer tüm işletim sistemi sürümlerinde: 394806|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |Üzerinde Windows 10 Creators güncelleştirmesi yalnızca: 460798<br/><br/> Diğer tüm işletim sistemi sürümlerinde: 460805 | .NET framework 4.7 |
    |Windows 10 Fall Creators Update üzerinde yalnızca: 461308<br/><br/> Diğer tüm işletim sistemi sürümlerinde: 461310 | .NET framework 4.7.1 |
    |Yalnızca Windows 10 Nisan 2018 güncelleştirmesi: 461808<br/><br/> Diğer tüm işletim sistemi sürümlerinde: 461814| .NET framework 4.7.2 |
    
<a name="net_c"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a>(.NET Framework 1-4) kod içinde kayıt defterini sorgulayarak .NET Framework sürümlerini bulmak için

- Kullanım <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> Software\Microsoft\NET Framework Setup\NDP\ subkey under HKEY_LOCAL_MACHINE Windows kayıt defterinde erişmek için sınıf.

     Aşağıdaki kod, bu sorgunun bir örneğini gösterir.

    > [!NOTE]
    > Bu kodu nasıl algılanacağını göstermez [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya üzeri. Denetleme `Release` önceki bölümde açıklandığı gibi bu sürümleri algılamak için DWORD. Algılayan kod için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya sonraki sürümlerinde, bu makalenin sonraki bölümüne bakın.

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

     Örnekte aşağıdakine benzer bir çıktı oluşturulur:

    ```
    v2.0.50727  2.0.50727.4016  SP2
    v3.0  3.0.30729.4037  SP2
    v3.5  3.5.30729.01  SP1
    v4
      Client  4.0.30319
      Full  4.0.30319
    ```

<a name="net_d"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a>(.NET Framework 4.5 ve üstü) kod içinde kayıt defterini sorgulayarak .NET Framework sürümlerini bulmak için

1. Varlığını `Release` DWORD .NET Framework 4.5 veya sonraki bir bilgisayarda yüklü olduğunu gösterir. Anahtar sözcüğü değerini yüklü olan sürümü gösterir. Bu anahtar sözcük denetlemek için kullanmak <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> ve <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> yöntemlerinin <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> Windows kayıt defterinde HKEY_LOCAL_MACHINE altındaki Software\Microsoft\NET Framework Setup\NDP\v4\Full alt anahtarına erişmek için sınıf.

2. Değerini kontrol edin `Release` yüklenen sürümü belirlemek için anahtar sözcüğü. İleri uyumlu olacak şekilde tabloda listelenen değerler eşit veya büyük bir değer denetleyebilirsiniz. .NET Framework sürümleri şunlardır ve ilişkili `Release` anahtar sözcükleri.

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |Sürüm|Yayın DWORD değeri|
    |-------------|--------------------------------|
    |.NET Framework 4.5|378389|
    |.NET framework 4.5.1 Windows 8.1 ile yüklü|378675|
    |.NET framework 4.5.1 Windows 8, Windows 7 SP1 veya Windows Vista SP2 yüklü|378758|
    |.NET Framework 4.5.2|379893|
    |.NET framework 4.6 ile Windows 10 yüklü|393295|
    |Diğer tüm Windows işletim sistemi sürümlerinde yüklü .NET framework 4.6|393297|
    |.NET framework 4.6.1 yüklü Windows 10'da|394254|
    |.NET framework 4.6.1 yüklü diğer tüm Windows işletim sistemi sürümlerinde|394271|
    |.NET framework 4.6.2, Windows 10 Yıldönümü güncelleştirmesi ve Windows Server 2016 yüklü|394802|
    |.NET framework 4.6.2 diğer tüm Windows işletim sistemi sürümlerinde yüklü|394806|
    |Windows 10 Creators Update üzerinde yüklü olan .NET framework 4.7|460798|
    |Diğer tüm Windows işletim sistemi sürümlerinde yüklü .NET framework 4.7|460805|
    |.NET framework 4.7.1 Windows 10 Fall Creators Update üzerinde yüklü|461308|
    |.NET framework 4.7.1 diğer tüm Windows işletim sistemi sürümlerinde yüklü|461310|
    |.NET framework Windows yüklü 4.7.2 10 Nisan 2018 güncelleştirmesi|461808|
    |.NET framework yüklü diğer tüm Windows işletim sistemi sürümlerinde 4.7.2|461814|
    
     Aşağıdaki örnek denetimlerini `Release` belirlemek için kayıt defteri değerindeki olmadığını [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya .NET Framework'ün daha sonraki bir sürümü yüklü.

     [!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
     [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

     Bu örnek, sürüm denetimi için önerilen yöntem aşağıda verilmiştir:

    - Denetlediği olup olmadığını değerini `Release` giriş *büyüktür veya eşittir* bilinen yayın anahtarları değeri.

    - Eski sürümü için en son sürüm sırayla denetler.

<a name="ps_a"></a> 
## <a name="to-check-for-a-minimum-required-net-framework-version-by-querying-the-registry-in-powershell-net-framework-45-and-later"></a>PowerShell (.NET Framework 4.5 ve üzeri) içinde kayıt defterini sorgulayarak için gereken en düşük .NET Framework sürümü denetlemek için

- Aşağıdaki örnek değerini denetler `Release` belirlemek için anahtar sözcüğü olup olmadığını .NET Framework 4.6.2 veya üzeri yüklü, Windows işletim sistemi sürümü bakılmaksızın (döndüren `True` etkinleştirilmişse ve `False` yoksa).

    ```PowerShell
    Get-ChildItem "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\" | Get-ItemPropertyValue -Name Release | ForEach-Object { $_ -ge 394802 } 
    ```

    Değiştirebilirsiniz `394802` için farklı bir gerekli en düşük .NET Framework sürüm denetlemek için aşağıdaki tabloda önceki örnekte başka bir değere sahip.
  
    |Sürüm|En düşük yayın DWORD değeri|
    |-------------|--------------------------------|
    |.NET Framework 4.5|378389|
    |.NET Framework 4.5.1|378675|
    |.NET Framework 4.5.2|379893|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|393295|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|394254|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|394802|
    |.NET framework 4.7|460798|
    |.NET framework 4.7.1|461308|
    |.NET framework 4.7.2|461808|

<a name="clr_a"></a> 
## <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a>Clrver aracını kullanarak geçerli çalışma zamanı sürümünü bulmak için

- Bilgisayarda ortak dil çalışma zamanının hangi sürümlerinin yüklü olduğunu saptamak için CLR Sürüm Aracı'nı (Clrver.exe) kullanın.

     Bir Visual Studio komut isteminden girin `clrver`. Bu komut aşağıdakine benzer bir çıktı oluşturur:

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     Bu aracı kullanma hakkında daha fazla bilgi için bkz. [Clrver.exe (CLR sürüm aracı)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).

<a name="clr_b"></a> 
## <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a>Kod içinde Ortam sınıfını sorgulayarak geçerli çalışma zamanı sürümünü bulmak için

- Sorgu <xref:System.Environment.Version%2A?displayProperty=nameWithType> almak için özellik bir <xref:System.Version> şu anda kodu yürüten çalışma zamanının sürümünü tanımlayan nesne. Kullanabileceğiniz <xref:System.Version.Major%2A?displayProperty=nameWithType> (örneğin, "4" sürüm 4.0 için), ana sürüm tanıtıcısını almak için özellik <xref:System.Version.Minor%2A?displayProperty=nameWithType> (örneğin, "0" sürüm 4.0 için), alt sürüm tanıtıcısını almak için özellik veya <xref:System.Object.ToString%2A?displayProperty=nameWithType> tüm sürümü almak için yöntemi dize ("aşağıdaki kodda gösterildiği gibi 4.0.30319.18010"). Bu özellik, kodu şu anda yürüten çalışma zamanı sürümünü gösteren tek bir değer döndürür; diğer sürümleri bilgisayarda yüklü çalışma zamanı derleme sürümleri döndürmez.

     4, 4.5, 4.5.1 ve 4.5.2'yi, .NET Framework sürümleri için <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği döndürür bir <xref:System.Version> nesnenin dize temsili olan form `4.0.30319.xxxxx`. .NET Framework 4.6 ve daha sonra bu biçimde `4.0.30319.42000`.

    > [!IMPORTANT]
    > İçin [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve kullanarak daha sonra önermiyoruz <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği çalışma zamanı sürümünü algılayamaz. Bunun yerine, kayıt defteri sorgu açıklandığı öneririz [(.NET Framework 4.5 ve üstü) kod içinde kayıt defterini sorgulayarak .NET Framework sürümlerini bulmak için](#net_d) bu makalenin önceki kısımlarında bölümü.

     İşte bir örnek sorgulama <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği çalışma zamanı sürüm bilgileri için:

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

     Örnekte aşağıdakine benzer bir çıktı oluşturulur:

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a>Ayrıca bkz.

[Nasıl yapılır: Hangi .NET Framework Güncelleştirmelerinin Yüklü Olduğunu Belirleme](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
[Geliştiriciler için .NET Framework'ü yükleme](../../../docs/framework/install/guide-for-developers.md)  
[Sürümler ve Bağımlılıklar](~/docs/framework/migration-guide/versions-and-dependencies.md)  
