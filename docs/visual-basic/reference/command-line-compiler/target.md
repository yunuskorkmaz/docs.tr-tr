---
title: -target
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
ms.openlocfilehash: bd79d95a18fb1935d97fff2d1b2c7767752b9765
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351727"
---
# <a name="-target-visual-basic"></a>-target (Visual Basic)

Derleyici çıktısının biçimini belirtir.

## <a name="syntax"></a>Sözdizimi

```console
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}
```

## <a name="remarks"></a>Açıklamalar

Aşağıdaki tablo `-target` seçeneğinin etkisini özetler.

|**Seçeneği**|**Durum**|
|----------------|------------------|
|`-target:exe`|Derleyicinin yürütülebilir bir konsol uygulaması oluşturmasına neden olur.<br /><br /> `-target` seçeneği belirtilmediğinde bu varsayılan seçenektir. Yürütülebilir dosya bir. exe uzantısıyla oluşturulur.<br /><br /> Aksi takdirde, `/out` seçeneğiyle belirtilmediği takdirde, çıkış dosyası adı `Sub Main` yordamını içeren giriş dosyasının adını alır.<br /><br /> Bir. exe dosyasına derlenen kaynak kodu dosyalarında yalnızca bir `Sub Main` yordamı gereklidir. Hangi sınıfın `Sub Main` yordamını içerdiğini belirtmek için `-main` derleyici seçeneğini kullanın.|
|`-target:library`|Derleyicinin dinamik bağlantı kitaplığı (DLL) oluşturmasına neden olur.<br /><br /> Dinamik bağlantı kitaplığı dosyası bir. dll uzantısıyla oluşturulur.<br /><br /> Aksi takdirde, `-out` seçeneğiyle belirtilmediği takdirde, çıkış dosyası adı ilk giriş dosyasının adını alır.<br /><br /> Bir DLL derlerken `Sub Main` yordam gerekli değildir.|
|`-target:module`|Derleyicinin bir derlemeye eklenebilecek bir modül oluşturmasına neden olur.<br /><br /> Çıkış dosyası. netmodule uzantısıyla oluşturulur.<br /><br /> .NET ortak dil çalışma zamanı, derlemesi olmayan bir dosyayı yükleyemez. Ancak, `-reference`kullanarak bu tür bir dosyayı derlemenin derleme bildirimine ekleyebilirsiniz.<br /><br /> Bir modüldeki kod, başka bir modüldeki iç türlere başvurduğunda, her iki modülün `-reference`kullanılarak bir derleme bildirimine dahil olması gerekir.<br /><br /> [-Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) seçeneği bir modülden meta verileri içeri aktarır.|
|`-target:winexe`|Derleyicinin yürütülebilir bir Windows tabanlı uygulama oluşturmasına neden olur.<br /><br /> Yürütülebilir dosya bir. exe uzantısıyla oluşturulur. Windows tabanlı bir uygulama, .NET Framework sınıf kitaplığından veya Windows API 'Leriyle bir kullanıcı arabirimi sağlayan bir uygulamadır.<br /><br /> Aksi takdirde, `-out` seçeneğiyle belirtilmediği takdirde, çıkış dosyası adı `Sub Main` yordamını içeren giriş dosyasının adını alır.<br /><br /> Bir. exe dosyasına derlenen kaynak kodu dosyalarında yalnızca bir `Sub Main` yordamı gereklidir. Kodunuzun `Sub Main` yordamına sahip birden fazla sınıfı olduğu durumlarda, hangi sınıfın `Sub Main` yordamını içerdiğini belirtmek için `-main` derleyici seçeneğini kullanın|
|`-target:appcontainerexe`|Derleyicinin bir uygulama kapsayıcısında çalıştırılması gereken yürütülebilir bir Windows tabanlı uygulama oluşturmasına neden olur. Bu ayar, Windows 8. x Mağazası uygulamaları için kullanılmak üzere tasarlanmıştır.<br /><br /> **Appcontainerexe** ayarı, [taşınabilir yürütülebilir](/windows/desktop/Debug/pe-format) dosyanın Özellikler alanında bir bit ayarlar. Bu bit, uygulamanın bir uygulama kapsayıcısında çalıştırılması gerektiğini gösterir. Bu bit ayarlandığında, `CreateProcess` metodu uygulamayı bir uygulama kapsayıcısı dışında başlatmaya çalışırsa bir hata oluşur. Bu bit ayarından itibaren **-target: appcontainerexe** eşittir **-target: winexe**.<br /><br /> Yürütülebilir dosya bir. exe uzantısıyla oluşturulur.<br /><br /> Aksi takdirde, `-out` seçeneğini kullanarak aksini belirtmediğiniz takdirde, çıkış dosyası adı `Sub Main` yordamını içeren giriş dosyasının adını alır.<br /><br /> Bir. exe dosyasına derlenen kaynak kodu dosyalarında yalnızca bir `Sub Main` yordamı gereklidir. Kodunuz `Sub Main` yordamına sahip birden fazla sınıf içeriyorsa, hangi sınıfın `Sub Main` yordamını içerdiğini belirtmek için `-main` derleyici seçeneğini kullanın|
|`-target:winmdobj`|Derleyicinin Windows Çalışma Zamanı ikili (. winmd) dosyasına dönüştürebileceğiniz bir ara dosya oluşturmasına neden olur. . Winmd dosyası, yönetilen dil programlarına ek olarak JavaScript C++ ve programlar tarafından tüketilebilir.<br /><br /> Ara dosya bir. winmdobj uzantısıyla oluşturulur.<br /><br /> Aksi takdirde, `-out` seçeneğini kullanarak aksini belirtmediğiniz takdirde, çıkış dosyası adı ilk giriş dosyasının adını alır. `Sub Main` yordam gerekli değildir.<br /><br /> . Winmdobj dosyası, Windows meta verileri (WinMD) dosyası üretmek için <xref:Microsoft.Build.Tasks.WinMDExp> dışa aktarma aracının girişi olarak kullanılmak üzere tasarlanmıştır. WinMD dosyası bir. winmd uzantısına sahiptir ve hem özgün kitaplıktan hem de JavaScript, C++ve Windows çalışma zamanı kullanılan winmd tanımlarındaki kodu içerir.|

`-target:module`belirtmediğiniz takdirde `-target`, bir .NET Framework derleme bildiriminin bir çıkış dosyasına eklenmesine neden olur.

Her Vbc. exe örneği, en çok bir çıkış dosyası üretir. `-out` veya birden çok kez `-target` gibi bir derleyici seçeneği belirtirseniz, derleyici işlemlerinin son bir etkisi olur. Bir derlemedeki tüm dosyalar hakkındaki bilgiler bildirime eklenir. `-target:module` ile oluşturulanlar dışındaki tüm çıkış dosyaları, bildirimde derleme meta verileri içerir. Meta verileri bir çıkış dosyasında görüntülemek için [ıldadsm. exe (IL Disassembler)](../../../framework/tools/ildasm-exe-il-disassembler.md) kullanın.

`-target` kısa biçimi `-t`.

### <a name="to-set--target-in-the-visual-studio-ide"></a>Visual Studio IDE 'de set-Target

1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Uygulama** sekmesine tıklayın.

3. **Uygulama türü** kutusunda değeri değiştirin.

## <a name="example"></a>Örnek

Aşağıdaki kod, `in.dll`oluşturarak `in.vb`derler:

```console
vbc -target:library in.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-Out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [-başvuru (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)
- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
