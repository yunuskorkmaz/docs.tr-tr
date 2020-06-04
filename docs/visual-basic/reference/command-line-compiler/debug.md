---
title: -debug
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
ms.openlocfilehash: 60c6e512a648f093bb9c70b5af86d5719e544adc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408731"
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

## <a name="arguments"></a>Bağımsız değişkenler

|Terim|Tanım|
|---|---|
|`+`&#124;`-`|İsteğe bağlı. `+` `-debug` Derleyicinin hata ayıklama bilgilerini oluşturmasını ve bir. pdb dosyasına yerleştirmesini sağlar. Belirtme `-` , belirtilmemekle aynı etkiye sahiptir `-debug` .|
|`full`&#124;`pdbonly`|İsteğe bağlı. Derleyici tarafından oluşturulan hata ayıklama bilgilerinin türünü belirtir. Belirtmezseniz, varsayılan olarak, `-debug:pdbonly` `full` çalışan programa bir hata ayıklayıcı eklemenize olanak sağlar. `pdbonly`Bağımsız değişken, program hata ayıklayıcıda başlatıldığında kaynak kodu hata ayıklamasına izin verir, ancak yalnızca çalışan program hata ayıklayıcıya eklendiğinde derleme dili kodunu görüntüler.|

## <a name="remarks"></a>Açıklamalar

Hata ayıklama derlemeleri oluşturmak için bu seçeneği kullanın. `-debug`, Veya belirtmezseniz, `-debug+` `-debug:full` programınızın çıkış dosyasında hata ayıklaması yapamazsınız.

Varsayılan olarak, hata ayıklama bilgileri yayılmaz ( `-debug-` ). Hata ayıklama bilgilerini göstermek için `-debug` veya belirtin `-debug+` .

Bir uygulamanın hata ayıklama performansını yapılandırma hakkında daha fazla bilgi için bkz. [bir görüntüyü hata ayıklamayı kolaylaştırın](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).

|Visual Studio tümleşik geliştirme ortamında ayarlamak için-hata ayıklayın|
|---|
|1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **Derle** sekmesine tıklayın.<br />3. **Gelişmiş derleme seçenekleri**'ne tıklayın.<br />4. **hata ayıklama bilgisi oluştur** kutusundaki değeri değiştirin.|

## <a name="example"></a>Örnek

Aşağıdaki örnek hata ayıklama bilgilerini çıkış dosyasına yerleştirir `App.exe` .

```console
vbc -debug -out:app.exe test.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [-bugreport](bugreport.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
