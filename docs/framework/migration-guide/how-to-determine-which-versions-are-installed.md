---
title: Hangi .NET Framework sürümlerinin yüklendiğini belirleme
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: b860aac01780acb67c53e822eff478b78198996b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738196"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme

Kullanıcılar bilgisayarlarına .NET Framework birden çok sürümünü [yükleyebilir](../install/index.md) ve çalıştırabilir. Uygulamanızı geliştirirken veya dağıtırken, kullanıcının bilgisayarında hangi .NET Framework sürümlerinin yüklü olduğunu bilmeniz gerekebilir.

.NET Framework, sürümü ayrı olan iki ana bileşenden oluşur:

- Uygulamalarınız için işlevsellik sağlayan tür ve kaynak koleksiyonları olan derlemeler kümesi. .NET Framework ve derlemeler aynı sürüm numarasını paylaşır.

- Uygulamanızın kodunu yöneten ve yürüten ortak dil çalışma zamanı (CLR). CLR kendi sürüm numarasıyla tanımlanır (bkz. [sürümler ve bağımlılıklar](versions-and-dependencies.md)).

> [!NOTE]
> .NET Framework'ün her yeni sürümü önceki sürümlerdeki özellikleri korur ve yeni özellikler ekler. .NET Framework birden çok sürümünü aynı anda tek bir bilgisayara yükleyebilirsiniz; Yani, önceki sürümleri kaldırmak zorunda kalmadan .NET Framework yükleyebilirsiniz. Genel olarak, kullandığınız bir uygulama belirli bir sürüme bağlı olabileceğinden ve bu sürüm kaldırılırsa kesintiye uğraabileceğinden, .NET Framework önceki sürümlerini kaldırmamanız gerekir.
>
> .NET Framework sürümü ile CLR sürümü arasında bir fark vardır:
>
> - .NET Framework sürümü, .NET Framework sınıf kitaplığını oluşturan derlemeler kümesini temel alır. Örneğin, .NET Framework sürümler 4,5, 4.6.1 ve 4.7.2 ' i içerir.
> - CLR sürümü .NET Framework uygulamalarının çalıştırıldığı çalışma zamanına dayalıdır. Tek bir CLR sürümü genellikle birden çok .NET Framework sürümü destekler. Örneğin, CLR sürüm 4.0.30319. *xxxxx* , 42000 .NET Framework sürümlerini destekler; burada *xxxxx* , ' den küçük ve CLR sürüm 4.0.30319.42000 .NET Framework 4,6 ' den başlayarak .NET Framework sürümlerini destekler.
>
> Sürümler hakkında daha fazla bilgi için bkz. [.NET Framework sürümler ve bağımlılıklar](versions-and-dependencies.md).

Kayıt defteri, bir bilgisayarda yüklü .NET Framework sürümlerinin bir listesini içerir. Kayıt defterini görüntülemek veya kodu kullanarak sorgulamak için kayıt defteri düzenleyicisini kullanabilirsiniz:

- Daha yeni .NET Framework sürümlerini bul (4,5 ve üzeri):

  - [.NET Framework sürümlerini bulmak için kayıt defteri düzenleyicisini kullanın](#net_b)
  - [.NET Framework sürümleri için kayıt defterini sorgulamak üzere kodu kullanma](#net_d)
  - [.NET Framework sürümleri için kayıt defterini sorgulamak üzere PowerShell 'i kullanma](#ps_a)

- Eski .NET Framework sürümlerini bul (1 ile 4 arasında):

  - [.NET Framework sürümlerini bulmak için kayıt defteri düzenleyicisini kullanın](#net_a)
  - [.NET Framework sürümleri için kayıt defterini sorgulamak üzere kodu kullanma](#net_c)

Bir bilgisayarda yüklü olan CLR sürümlerinin bir listesini almak için bir araç veya kod kullanın:

- [Clrver aracını kullanma](#clr_a)
- [Ortam sınıfını sorgulamak için kodu kullanma](#clr_b)

.NET Framework her sürümü için yüklü güncelleştirmeleri algılama hakkında bilgi için bkz. [nasıl yapılır: hangi .NET Framework güncelleştirmelerinin yükleneceğini belirleme](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="find-newer-net-framework-versions-45-and-later"></a>Daha yeni .NET Framework sürümlerini bul (4,5 ve üzeri)

Kayıt Defteri Düzenleyicisi 'ni kullanarak kayıt defterindeki sürüm bilgilerini bulabilir veya kayıt defterini programlı bir şekilde sorgulayabilirsiniz.

<a name="net_b"></a>

### <a name="use-registry-editor"></a>Kayıt Defteri Düzenleyicisi 'Ni kullan

1. **Başlat** menüsünde, **Çalıştır**' ı seçin, *Regedit*' i girin ve **Tamam**' ı seçin.

     Regedit 'i çalıştırmak için yönetici kimlik bilgilerine sahip olmanız gerekir.

2. Kayıt Defteri Düzenleyicisi 'nde, aşağıdaki alt anahtarı açın: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**. **Tam** alt anahtar yoksa, .NET Framework 4,5 veya sonraki bir sürümü yüklü değildir.

    > [!NOTE]
    > Kayıt defterindeki **net Framework kurulum** klasörü bir *noktayla başlamaz.*

3. **Yayın**ADLı bir DWORD girişini denetleyin. Varsa, .NET Framework 4,5 veya sonraki bir sürümü yüklemiş olursunuz. Değeri, .NET Framework belirli bir sürümüne karşılık gelen bir sürüm anahtarıdır. Aşağıdaki şekilde, örneğin, **Sürüm** girişinin değeri 378389 ' dir. bu, .NET Framework 4,5 ' in sürüm anahtarıdır.

   ![.NET Framework 4,5 için kayıt defteri girişi](./media/clr-installdir.png ".NET Framework 4,5 için kayıt defteri girişi")

Aşağıdaki tabloda, .NET Framework 4,5 ve üzeri sürümler için tek tek işletim sistemlerindeki **Sürüm** DWORD değeri listelenmektedir.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|.NET Framework sürümü|Yayın DWORD değeri|
|--------------------------------|-------------|
|.NET Framework 4.5|Tüm Windows işletim sistemleri: 378389|
|.NET Framework 4.5.1|Windows 8.1 ve Windows Server 2012 R2 'de: 378675<br />Diğer tüm Windows işletim sistemlerinde: 378758|
|.NET Framework 4.5.2|Tüm Windows işletim sistemleri: 379893|
|.NET Framework 4.6|Windows 10:393295 ' de<br />Diğer tüm Windows işletim sistemlerinde: 393297|
|.NET Framework 4.6.1|Windows 10 Kasım güncelleştirme sistemlerinde: 394254<br />Diğer tüm Windows işletim sistemlerinde (Windows 10 dahil): 394271|
|.NET Framework 4.6.2|Windows 10 yıldönümü güncelleştirmesi ve Windows Server 2016:394802<br />Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 394806|
|.NET Framework 4,7|Windows 10 Creators Update üzerinde: 460798<br />Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 460805|
|.NET Framework 4.7.1|Windows 10 Fall Creators Update ve Windows Server, sürüm 1709:461308<br/>Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 461310|
|.NET Framework 4.7.2|Windows 10 Nisan 2018 güncelleştirmesi ve Windows Server, sürüm 1803:461808<br/>Windows 10 Nisan 2018 güncelleştirmesi ve Windows Server, sürüm 1803 dışındaki tüm Windows işletim sistemlerinde: 461814|
|.NET Framework 4,8|Windows 10 Mayıs 2019 güncelleştirmesi ve Windows 10 Kasım 2019 güncelleştirmesi: 528040<br/>Diğer tüm Windows işletim sistemlerinde (diğer Windows 10 işletim sistemleri dahil): 528049|

#### <a name="specific-version"></a>Belirli sürüm

*Belirli* bir .NET Framework sürümünün Windows işletim sisteminin belirli bir sürümüne yüklenip yüklenmediğini öğrenmek Için, **yayın** DWORD değerinin tabloda listelenen değere *eşit* olup olmadığını test edin. Örneğin, Windows 10 sisteminde .NET Framework 4,6 olup olmadığını anlamak için, 393295 ' *e eşit* olan bir **yayın** değeri için test edin.

#### <a name="minimum-version"></a>En düşük sürüm

.NET Framework *En düşük* sürümünün mevcut olup olmadığını anlamak için önceki tablodan bu sürüm için en küçük **yayın** DWORD değerini kullanın. (Kolaylık olması için, aşağıdaki tabloda yer alan minimum değerler de listelenmiştir.)

Örneğin, uygulamanız .NET Framework 4,8 veya sonraki bir sürümde çalışıyorsa, 528040 ' *den büyük veya buna eşit* bir **yayın** DWORD değeri testi yapın.

|.NET Framework sürümü|En küçük yayın DWORD değeri|
|--------------------------------|-------------|
|.NET Framework 4.5|378389|
|.NET Framework 4.5.1|378675|
|.NET Framework 4.5.2|379893|
|.NET Framework 4.6|393295|
|.NET Framework 4.6.1|394254|
|.NET Framework 4.6.2|394802|
|.NET Framework 4,7|460798|
|.NET Framework 4.7.1|461308|
|.NET Framework 4.7.2|461808|
|.NET Framework 4,8|528040|

#### <a name="multiple-versions"></a>Birden çok sürüm

Birden çok sürümü test etmek için, en son .NET Framework sürümü için daha küçük DWORD değerinden *büyük veya ona eşit* bir değer için test yaparak başlayın ve ardından değeri, sonraki her önceki sürüm için daha küçük DWORD değeri ile karşılaştırın. Örneğin, uygulamanız .NET Framework 4,7 veya üzeri bir sürüm gerektiriyorsa ve mevcut .NET Framework sürümünü belirleyebilmek istiyorsanız, 461808 ' e *eşit veya* daha küçük olan bir **yayın** DWORD değeri için test yaparak BAŞLAYıN (daha küçük DWORD .NET Framework 4.7.2) değeri. Ardından, **yayın** DWORD değerini her bir sonraki .NET Framework sürümü için daha küçük bir değerle karşılaştırın.

<a name="net_d"></a>

### <a name="query-the-registry-using-code"></a>Kodu kullanarak kayıt defterini sorgulama

1. Windows kayıt defterindeki **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** alt anahtarına erişmek için <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> ve <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> yöntemlerini kullanın.

   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** alt anahtarındaki **Release** DWORD girişinin varlığı, bir bilgisayarda .NET Framework 4,5 veya sonraki bir sürümün yüklü olduğunu gösterir.

2. Yüklü sürümü öğrenmek için **yayın** girişinin değerini denetleyin. İleriye dönük olarak uyumlu olması için [.NET Framework sürüm tablosunda](#version_table)listelenen değerden daha büyük veya ona eşit bir değer olup olmadığını kontrol edin.

Aşağıdaki örnek, yüklü olan .NET Framework 4,5 ve sonraki sürümlerini bulmak için kayıt defterindeki **yayın** girişinin değerini denetler:

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

Bu örnek sürüm denetimi için önerilen yöntemi izler:

- **Yayın** girişi değerinin bilinen yayın anahtarlarının değerinden *büyük veya* bu değere eşit olup olmadığını denetler.

- En son sürümden en eski sürüme sırayla kontrol eder.

<a name="ps_a"></a>

### <a name="use-powershell-to-check-for-a-minimum-required-version"></a>Gerekli en düşük sürümü denetlemek için PowerShell 'i kullanın

**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** alt anahtarının **yayın** girişinin değerini denetlemek için PowerShell komutlarını kullanın.

Aşağıdaki örnekler, .NET Framework 4.6.2 veya sonraki bir sürümün yüklenip yüklenmediğini anlamak için **yayın** girişinin değerini denetler. Bu kod, yüklenmişse `True` döndürür ve yoksa `False`.

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

Farklı bir en düşük gerekli .NET Framework sürümünü denetlemek için örnekteki `394802` [.NET Framework sürüm tablosundan](#version_table)bir değer ile değiştirin. Bu sürüm için gösterilen en küçük değeri kullanın.

## <a name="find-older-net-framework-versions-1-through-4"></a>Eski .NET Framework sürümlerini bul (1 ile 4 arasında)

<a name="net_a"></a>

### <a name="use-registry-editor-older-framework-versions"></a>Kayıt Defteri Düzenleyicisi 'Ni kullan (eski Framework sürümleri)

1. **Başlat** menüsünde, **Çalıştır**' ı seçin, *Regedit*' i girin ve **Tamam**' ı seçin.

    Regedit 'i çalıştırmak için yönetici kimlik bilgilerine sahip olmanız gerekir.

2. Kayıt Defteri Düzenleyicisi 'nde, aşağıdaki alt anahtarı açın: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:

    - 1,1 ile 3,5 arasındaki .NET Framework sürümleri için, yüklü her sürüm **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** alt anahtarı altında bir alt anahtar olarak listelenir. Örneğin, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**. Sürüm numarası, sürüm alt anahtarının **Sürüm** girişinde bir değer olarak depolanır.

    - .NET Framework 4 için **Sürüm** girdisi **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** alt anahtarı, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** altındadır. alt anahtar veya her iki alt anahtarda.

    > [!NOTE]
    > Kayıt defterindeki **net Framework kurulum** klasörü bir noktayla başlamaz.

    Aşağıdaki şekilde, .NET Framework 3,5 için alt anahtar ve **Sürüm** girişi gösterilmektedir.

    ![3,5 .NET Framework için kayıt defteri girişi.](./media/net-4-and-earlier.png ".NET Framework 3,5 ve önceki sürümler")

<a name="net_c"></a>

### <a name="query-the-registry-using-code-older-framework-versions"></a>Kodu kullanarak kayıt defterini sorgulama (eski Framework sürümleri)

Windows kayıt defterindeki **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** alt anahtarına erişmek için <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> sınıfını kullanın.

Aşağıdaki örnek, yüklü .NET Framework 1 ila 4 sürümü bulur:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a>CLR sürümlerini bul

<a name="clr_a"></a>

### <a name="use-clrverexe"></a>Clrver. exe kullanma

Clr [Sürüm aracı 'nı (Clrver. exe)](../tools/clrver-exe-clr-version-tool.md) kullanarak bir bılgısayarda hangi CLR sürümlerinin yüklü olduğunu belirleme:

- [Visual Studio için Geliştirici Komut İstemi](../tools/developer-command-prompt-for-vs.md)`clrver`girin.

    Örnek çıktı:

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a>

### <a name="use-the-environment-class"></a>Ortam sınıfını kullanma

> [!IMPORTANT]
> .NET Framework 4,5 ve sonraki sürümlerinde, CLR sürümünü algılamak için <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliğini kullanmayın. Bunun yerine, kayıt defterini, [kodla .NET Framework sürümler 4,5 ve sonraki kısımlarında](#net_d)açıklandığı gibi sorgulayın.

1. <xref:System.Version> nesnesini almak için <xref:System.Environment.Version?displayProperty=nameWithType> özelliğini sorgulayın.

    Döndürülen `System.Version` nesnesi şu anda kodu yürüten çalışma zamanının sürümünü tanımlar. Derleme sürümlerini veya çalışma zamanının bilgisayarda yüklü olabilecek diğer sürümlerini döndürmez.

    .NET Framework sürümleri 4, 4,5, 4.5.1 ve 4.5.2 için, döndürülen <xref:System.Version> nesnesinin dize temsili 4.0.30319 biçimindedir. *xxxxx*, *xxxxx* 42000 ' den küçük. .NET Framework 4,6 ve sonraki sürümlerinde, 4.0.30319.42000 biçiminde olur.

2. `Version` nesnesine sahip olduktan sonra aşağıdaki gibi sorgulayın:

   - Ana yayın tanımlayıcısı için (örneğin, sürüm 4,0 için *4* ) <xref:System.Version.Major%2A?displayProperty=nameWithType> özelliğini kullanın.

   - Küçük yayın tanımlayıcısı için (örneğin, sürüm 4,0 için *0* ) <xref:System.Version.Minor%2A?displayProperty=nameWithType> özelliğini kullanın.

   - Tüm sürüm dizesi için (örneğin, *4.0.30319.18010*) <xref:System.Version.ToString%2A?displayProperty=nameWithType> yöntemini kullanın. Bu yöntem, kodu yürüten çalışma zamanının sürümünü yansıtan tek bir değer döndürür. Bu, bilgisayarda yüklü olabilecek derleme sürümlerini veya diğer çalışma zamanı sürümlerini döndürmez.

Aşağıdaki örnek CLR sürüm bilgilerini almak için <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliğini kullanır:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: hangi .NET Framework güncelleştirmelerinin yükleneceğini belirleme](how-to-determine-which-net-framework-updates-are-installed.md)
- [Geliştiriciler için .NET Framework yüklemesi](../install/guide-for-developers.md)
- [.NET Framework sürümleri ve bağımlılıklar](versions-and-dependencies.md)
