---
title: 'Nasıl yapılır: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme'
ms.date: 03/18/2019
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
ms.openlocfilehash: 74c68aec535515803b9048aeed8395b53a4aaa4b
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411050"
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
>- CLR sürümü, .NET Framework uygulamaları, üzerinde yürütme çalışma zamanı temel alır. Tek bir CLR sürümü, genellikle birden çok .NET Framework sürümlerini destekler. Örneğin, CLR sürüm 4.0.30319. *xxxxx* 4.5.2 aracılığıyla .NET Framework sürüm 4 ve 4.0.30319.42000 .NET Framework 4. 6'ile başlayan .NET Framework sürümlerini destekleyen CLR sürümünü destekler. 
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
    > **NET Framework Kurulum** klasörünü noktayla başlayan değil.

3. Adlı bir DWORD girişini denetleyin **yayın**. Varsa, ardından, .NET Framework 4.5 veya sonraki bir sürümünün yüklü olması. Değerini belirli bir .NET Framework sürümüne karşılık gelen bir yayın anahtardır. Aşağıdaki şekilde, örneğin değerini **yayın** girdidir *378389*, .NET Framework 4.5 için yayın anahtar olduğu. 

     ![.NET Framework 4.5 için kayıt defteri girişi](media/clr-installdir.png ".NET Framework 4.5 için kayıt defteri girişi")

Aşağıdaki tabloda en küçük değerini **yayın** her .NET Framework sürümü için giriş. Bu değerleri şu şekilde kullanabilirsiniz:

- Bir en düşük .NET Framework sürümü mevcut olup olmadığını belirlemek için test olmadığını **yayın** DWORD değeri kayıt defterinde bulundu *büyüktür veya eşittir* değeri tabloda listelenen. Örneğin, uygulamanız .NET Framework 4.7 veya üzeri gerektiriyorsa, en düşük sürüm anahtar değeri için test *460798*.

- Birden çok sürümü için test etmek için en son .NET Framework sürümü ile başlayın ve ardından her art arda gelen önceki sürümü için test.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|.NET Framework sürümü|Yayın DWORD değeri|
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
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
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

    .NET Framework sürüm 4, 4.5, 4.5.1 ve 4.5.2'yi, döndürülen dize gösterimi için <xref:System.Version> nenesindeki formun 4.0.30319. *xxxxx*. .NET Framework 4.6 ve sonraki sürümler için formun 4.0.30319.42000 sahiptir.    

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
