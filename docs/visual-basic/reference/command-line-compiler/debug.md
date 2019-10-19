---
title: /debug (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
ms.openlocfilehash: 0bcb4d3693d7a688cbf5c75212c3d409ea73a482
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581460"
---
# <a name="-debug-visual-basic"></a>-Debug (Visual Basic)

Derleyicinin hata ayıklama bilgileri oluşturmasına ve bunu çıkış dosyasına yerleştirmesine neden olur.

## <a name="syntax"></a>Sözdizimi

```console
-debug[+ | -]
```

veya

```console
-debug:[full | pdbonly]
```

## <a name="arguments"></a>Arguments

|Terim|Tanım|
|---|---|
|`+` &#124; `-`|İsteğe bağlı. @No__t_0 veya `/debug` belirtme derleyicinin hata ayıklama bilgileri oluşturmasına ve bir. pdb dosyasına yerleştirmesine neden olur. @No__t_0 belirtmek `/debug` Belirtmemeye yönelik aynı etkiye sahiptir.|
|`full` &#124; `pdbonly`|İsteğe bağlı. Derleyici tarafından oluşturulan hata ayıklama bilgilerinin türünü belirtir. @No__t_0 belirtmezseniz, varsayılan değer, çalışan programa bir hata ayıklayıcı eklemenize olanak sağlayan `full`. @No__t_0 bağımsız değişkeni, program hata ayıklayıcıda başlatıldığında kaynak kodu hata ayıklamasına izin verir, ancak yalnızca çalışan program hata ayıklayıcıya eklendiğinde derleme dili kodunu görüntüler.|

## <a name="remarks"></a>Açıklamalar

Hata ayıklama derlemeleri oluşturmak için bu seçeneği kullanın. @No__t_0, `/debug+` veya `/debug:full` belirtmezseniz, programınızın çıkış dosyasında hata ayıklaması yapamazsınız.

Varsayılan olarak, hata ayıklama bilgileri yayınlanmaz (`/debug-`). Hata ayıklama bilgilerini göstermek için `/debug` veya `/debug+` belirtin.

Bir uygulamanın hata ayıklama performansını yapılandırma hakkında daha fazla bilgi için bkz. [bir görüntüyü hata ayıklamayı kolaylaştırın](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).

|Visual Studio tümleşik geliştirme ortamında ayarlamak için-hata ayıklayın|
|---|
|1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **Derle** sekmesine tıklayın.<br />3. **Gelişmiş derleme seçenekleri**'ne tıklayın.<br />4. **hata ayıklama bilgisi oluştur** kutusundaki değeri değiştirin.|

## <a name="example"></a>Örnek

Aşağıdaki örnek hata ayıklama bilgilerini çıkış dosyasında `App.exe` olarak yerleştirir.

```console
vbc -debug -out:app.exe test.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
