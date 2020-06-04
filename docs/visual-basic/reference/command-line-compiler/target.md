---
title: -target
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
ms.openlocfilehash: 0ab28d55b2426a4efda112ab84da5e790909d565
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403076"
---
# <a name="-target-visual-basic"></a>-target (Visual Basic)

Derleyici çıktısının biçimini belirtir.

## <a name="syntax"></a>Sözdizimi

```console
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}
```

## <a name="remarks"></a>Açıklamalar

Aşağıdaki tablo, seçeneğinin etkisini özetler `-target` .

|**Seçeneği**|**Davranış**|
|----------------|------------------|
|`-target:exe`|Derleyicinin yürütülebilir bir konsol uygulaması oluşturmasına neden olur.<br /><br /> Hiçbir seçenek belirtilmediğinde bu varsayılan seçenektir `-target` . Yürütülebilir dosya bir. exe uzantısıyla oluşturulur.<br /><br /> Bu seçenekle aksi belirtilmedikçe `-out` , çıkış dosyası adı, yordamı içeren giriş dosyasının adını alır `Sub Main` .<br /><br /> `Sub Main`Bir. exe dosyasına derlenen kaynak kodu dosyalarında yalnızca bir yordam gereklidir. `-main`Yordamı hangi sınıfın içerdiğini belirtmek için derleyici seçeneğini kullanın `Sub Main` .|
|`-target:library`|Derleyicinin dinamik bağlantı kitaplığı (DLL) oluşturmasına neden olur.<br /><br /> Dinamik bağlantı kitaplığı dosyası bir. dll uzantısıyla oluşturulur.<br /><br /> Aksi belirtilmediği takdirde `-out` , çıkış dosyası adı ilk giriş dosyasının adını alır.<br /><br /> Bir DLL derlerken, bir `Sub Main` yordam gerekli değildir.|
|`-target:module`|Derleyicinin bir derlemeye eklenebilecek bir modül oluşturmasına neden olur.<br /><br /> Çıkış dosyası. netmodule uzantısıyla oluşturulur.<br /><br /> .NET ortak dil çalışma zamanı, derlemesi olmayan bir dosyayı yükleyemez. Ancak, bu tür bir dosyayı kullanarak bir derlemenin derleme bildirimine ekleyebilirsiniz `-reference` .<br /><br /> Bir modüldeki kod, başka bir modüldeki iç türlere başvurduğunda, her iki modülün kullanılarak bir derleme bildirimine dahil olması gerekir `-reference` .<br /><br /> [-Addmodule](addmodule.md) seçeneği bir modülden meta verileri içeri aktarır.|
|`-target:winexe`|Derleyicinin yürütülebilir bir Windows tabanlı uygulama oluşturmasına neden olur.<br /><br /> Yürütülebilir dosya bir. exe uzantısıyla oluşturulur. Windows tabanlı bir uygulama, .NET Framework sınıf kitaplığından veya Windows API 'Leriyle bir kullanıcı arabirimi sağlayan bir uygulamadır.<br /><br /> Bu seçenekle aksi belirtilmedikçe `-out` , çıkış dosyası adı, yordamı içeren giriş dosyasının adını alır `Sub Main` .<br /><br /> `Sub Main`Bir. exe dosyasına derlenen kaynak kodu dosyalarında yalnızca bir yordam gereklidir. Kodunuzun bir yordamı olan birden fazla sınıfı olduğu durumlarda `Sub Main` , `-main` yordamı hangi sınıfın içerdiğini belirtmek için derleyici seçeneğini kullanın `Sub Main`|
|`-target:appcontainerexe`|Derleyicinin bir uygulama kapsayıcısında çalıştırılması gereken yürütülebilir bir Windows tabanlı uygulama oluşturmasına neden olur. Bu ayar, Windows 8. x Mağazası uygulamaları için kullanılmak üzere tasarlanmıştır.<br /><br /> **Appcontainerexe** ayarı, [taşınabilir yürütülebilir](/windows/desktop/Debug/pe-format) dosyanın Özellikler alanında bir bit ayarlar. Bu bit, uygulamanın bir uygulama kapsayıcısında çalıştırılması gerektiğini gösterir. Bu bit ayarlandığında, `CreateProcess` yöntemi uygulama kapsayıcısı dışında uygulamayı başlatmaya çalışırsa bir hata oluşur. Bu bit ayarından itibaren **-target: appcontainerexe** eşittir **-target: winexe**.<br /><br /> Yürütülebilir dosya bir. exe uzantısıyla oluşturulur.<br /><br /> Aksi takdirde seçeneğini kullanarak belirtmediğiniz takdirde `-out` , çıkış dosyası adı, yordamı içeren giriş dosyasının adını alır `Sub Main` .<br /><br /> `Sub Main`Bir. exe dosyasına derlenen kaynak kodu dosyalarında yalnızca bir yordam gereklidir. Kodunuz, yordamı olan birden fazla sınıf içeriyorsa `Sub Main` , `-main` yordamı hangi sınıfın içerdiğini belirtmek için derleyici seçeneğini kullanın `Sub Main`|
|`-target:winmdobj`|Derleyicinin Windows Çalışma Zamanı ikili (. winmd) dosyasına dönüştürebileceğiniz bir ara dosya oluşturmasına neden olur. . Winmd dosyası, yönetilen dil programlarına ek olarak JavaScript ve C++ programları tarafından tüketilebilir.<br /><br /> Ara dosya bir. winmdobj uzantısıyla oluşturulur.<br /><br /> Aksi takdirde seçeneğini kullanarak belirtmediğiniz takdirde `-out` , çıkış dosyası adı ilk giriş dosyasının adını alır. Bir `Sub Main` yordam gerekli değildir.<br /><br /> . Winmdobj dosyası, <xref:Microsoft.Build.Tasks.WinMDExp> dışa aktarma aracının bir Windows meta verileri (WinMD) dosyası oluşturmak için giriş olarak kullanılmak üzere tasarlanmıştır. WinMD dosyası bir. winmd uzantısına sahiptir ve özgün kitaplıktan kodu ve JavaScript, C++ ve Windows Çalışma Zamanı kullandığı WinMD tanımlarını içerir.|

Belirtmediğiniz takdirde `-target:module` , `-target` bir .NET Framework derleme bildiriminin bir çıkış dosyasına eklenmesine neden olur.

Her Vbc. exe örneği, en çok bir çıkış dosyası üretir. Veya birden çok kez gibi bir derleyici seçeneği `-out` belirtirseniz `-target` , derleyici işlemlerinin son bir etkisi olur. Bir derlemedeki tüm dosyalar hakkındaki bilgiler bildirime eklenir. İle oluşturulanlar dışındaki tüm çıkış dosyaları `-target:module` , bildirimde derleme meta verileri içerir. Meta verileri bir çıkış dosyasında görüntülemek için [ıldadsm. exe (IL Disassembler)](../../../framework/tools/ildasm-exe-il-disassembler.md) kullanın.

Öğesinin kısa biçimi `-target` `-t` .

### <a name="to-set--target-in-the-visual-studio-ide"></a>Visual Studio IDE 'de set-Target

1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Uygulama** sekmesine tıklayın.

3. **Uygulama türü** kutusunda değeri değiştirin.

## <a name="example"></a>Örnek

Aşağıdaki kod derlenir `in.vb` , oluşturma `in.dll` :

```console
vbc -target:library in.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [-main](main.md)
- [-Out (Visual Basic)](out.md)
- [-başvuru (Visual Basic)](reference.md)
- [-addmodule](addmodule.md)
- [-moduleassemblyname](moduleassemblyname.md)
- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
