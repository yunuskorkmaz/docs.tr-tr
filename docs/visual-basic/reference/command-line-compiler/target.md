---
title: -target
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
ms.openlocfilehash: d186670489ada51fced67ff9adeb73b14909b664
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716684"
---
# <a name="-target-visual-basic"></a>-target (Visual Basic)

Derleyici çıktısının biçimini belirtir.

## <a name="syntax"></a>Sözdizimi

```console
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}
```

## <a name="remarks"></a>Açıklamalar

Aşağıdaki tablo, `-target` seçeneğinin etkisini özetler.

|**Seçeneği**|**Davranış**|
|----------------|------------------|
|`-target:exe`|Derleyicinin yürütülebilir bir konsol uygulaması oluşturmasına neden olur.<br /><br /> Hiçbir `-target` seçenek belirtilmediğinde bu varsayılan seçenektir. Yürütülebilir dosya bir. exe uzantısıyla oluşturulur.<br /><br /> Bu `-out` seçenekle aksi belirtilmedikçe, çıkış dosyası adı, `Sub Main` yordamı içeren giriş dosyasının adını alır.<br /><br /> Bir. `Sub Main` exe dosyasına derlenen kaynak kodu dosyalarında yalnızca bir yordam gereklidir. Yordamı hangi `-main` sınıfın içerdiğini belirtmek için derleyici seçeneğini kullanın. `Sub Main`|
|`-target:library`|Derleyicinin dinamik bağlantı kitaplığı (DLL) oluşturmasına neden olur.<br /><br /> Dinamik bağlantı kitaplığı dosyası bir. dll uzantısıyla oluşturulur.<br /><br /> Aksi `-out` belirtilmediği takdirde, çıkış dosyası adı ilk giriş dosyasının adını alır.<br /><br /> Bir DLL derlerken, bir `Sub Main` yordam gerekli değildir.|
|`-target:module`|Derleyicinin bir derlemeye eklenebilecek bir modül oluşturmasına neden olur.<br /><br /> Çıkış dosyası. netmodule uzantısıyla oluşturulur.<br /><br /> .NET ortak dil çalışma zamanı, derlemesi olmayan bir dosyayı yükleyemez. Ancak, bu tür bir dosyayı kullanarak `-reference`bir derlemenin derleme bildirimine ekleyebilirsiniz.<br /><br /> Bir modüldeki kod, başka bir modüldeki iç türlere başvurduğunda, her iki modülün kullanılarak `-reference`bir derleme bildirimine dahil olması gerekir.<br /><br /> [-Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) seçeneği bir modülden meta verileri içeri aktarır.|
|`-target:winexe`|Derleyicinin yürütülebilir bir Windows tabanlı uygulama oluşturmasına neden olur.<br /><br /> Yürütülebilir dosya bir. exe uzantısıyla oluşturulur. Windows tabanlı bir uygulama, .NET Framework sınıf kitaplığından veya Windows API 'Leriyle bir kullanıcı arabirimi sağlayan bir uygulamadır.<br /><br /> Bu `-out` seçenekle aksi belirtilmedikçe, çıkış dosyası adı, `Sub Main` yordamı içeren giriş dosyasının adını alır.<br /><br /> Bir. `Sub Main` exe dosyasına derlenen kaynak kodu dosyalarında yalnızca bir yordam gereklidir. Kodunuzun bir `Sub Main` yordamı olan birden fazla sınıfı olduğu durumlarda, `-main` `Sub Main` yordamı hangi sınıfın içerdiğini belirtmek için derleyici seçeneğini kullanın|
|`-target:appcontainerexe`|Derleyicinin bir uygulama kapsayıcısında çalıştırılması gereken yürütülebilir bir Windows tabanlı uygulama oluşturmasına neden olur. Bu ayar, Windows 8. x Mağazası uygulamaları için kullanılmak üzere tasarlanmıştır.<br /><br /> **Appcontainerexe** ayarı, [taşınabilir yürütülebilir](/windows/desktop/Debug/pe-format) dosyanın Özellikler alanında bir bit ayarlar. Bu bit, uygulamanın bir uygulama kapsayıcısında çalıştırılması gerektiğini gösterir. Bu bit ayarlandığında, `CreateProcess` yöntemi uygulama kapsayıcısı dışında uygulamayı başlatmaya çalışırsa bir hata oluşur. Bu bit ayarından itibaren **-target: appcontainerexe** eşittir **-target: winexe**.<br /><br /> Yürütülebilir dosya bir. exe uzantısıyla oluşturulur.<br /><br /> Aksi takdirde `-out` seçeneğini kullanarak belirtmediğiniz takdirde, çıkış dosyası adı, `Sub Main` yordamı içeren giriş dosyasının adını alır.<br /><br /> Bir. `Sub Main` exe dosyasına derlenen kaynak kodu dosyalarında yalnızca bir yordam gereklidir. Kodunuz, `Sub Main` yordamı olan birden fazla sınıf içeriyorsa, `-main` `Sub Main` yordamı hangi sınıfın içerdiğini belirtmek için derleyici seçeneğini kullanın|
|`-target:winmdobj`|Derleyicinin Windows Çalışma Zamanı ikili (. winmd) dosyasına dönüştürebileceğiniz bir ara dosya oluşturmasına neden olur. . Winmd dosyası, yönetilen dil programlarına ek olarak JavaScript ve C++ programları tarafından tüketilebilir.<br /><br /> Ara dosya bir. winmdobj uzantısıyla oluşturulur.<br /><br /> Aksi takdirde `-out` seçeneğini kullanarak belirtmediğiniz takdirde, çıkış dosyası adı ilk giriş dosyasının adını alır. Bir `Sub Main` yordam gerekli değildir.<br /><br /> . Winmdobj dosyası, <xref:Microsoft.Build.Tasks.WinMDExp> dışa aktarma aracının bir Windows meta verileri (WinMD) dosyası oluşturmak için giriş olarak kullanılmak üzere tasarlanmıştır. WinMD dosyası bir. winmd uzantısına sahiptir ve özgün kitaplıktan kodu ve JavaScript, C++ ve Windows Çalışma Zamanı kullandığı WinMD tanımlarını içerir.|

Belirtmediğiniz `-target:module`takdirde, `-target` bir .NET Framework derleme bildiriminin bir çıkış dosyasına eklenmesine neden olur.

Her Vbc. exe örneği, en çok bir çıkış dosyası üretir. `-out` Veya `-target` birden çok kez gibi bir derleyici seçeneği belirtirseniz, derleyici işlemlerinin son bir etkisi olur. Bir derlemedeki tüm dosyalar hakkındaki bilgiler bildirime eklenir. İle `-target:module` oluşturulanlar dışındaki tüm çıkış dosyaları, bildirimde derleme meta verileri içerir. Meta verileri bir çıkış dosyasında görüntülemek için [ıldadsm. exe (IL Disassembler)](../../../framework/tools/ildasm-exe-il-disassembler.md) kullanın.

Öğesinin `-target` kısa biçimi `-t`.

### <a name="to-set--target-in-the-visual-studio-ide"></a>Visual Studio IDE 'de set-Target

1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Uygulama** sekmesine tıklayın.

3. **Uygulama türü** kutusunda değeri değiştirin.

## <a name="example"></a>Örnek

Aşağıdaki kod derlenir `in.vb`, oluşturma `in.dll`:

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
