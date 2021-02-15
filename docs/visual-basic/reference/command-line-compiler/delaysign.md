---
description: Daha fazla bilgi edinin:-delaysign
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: fc3e52f63431da870355e369e6ffeb8b7b14c5ab
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461508"
---
# <a name="-delaysign"></a>-delaysign

Derlemenin tamamen veya kısmen imzalanacağını belirtir.

## <a name="syntax"></a>Söz dizimi

```console
-delaysign[+ | -]
```

## <a name="arguments"></a>Bağımsız değişkenler

`+` &#124; `-`  
İsteğe bağlı. `-delaysign-`Tam olarak imzalanan bir derleme istiyorsanız kullanın. `-delaysign+`Ortak anahtarı derlemeye yerleştirmek ve imzalı karma için alan ayırmak istiyorsanız kullanın. Varsayılan değer: `-delaysign-`.

## <a name="remarks"></a>Açıklamalar

`-delaysign` [-Keyfile](keyfile.md) veya [-keycontainer](keycontainer.md)ile kullanılmamışsa seçeneğinin etkisi yoktur.

Tam olarak imzalanan bir derleme istediğinizde, derleyici bildirimi içeren dosyayı (derleme meta verileri) karma hale getirir ve bu karmayı özel anahtarla imzalar. Elde edilen dijital imza, bildirimi içeren dosyada depolanır. Bir derlemenin gecikmesi gecikmeli olduğunda, derleyici imzayı hesaplamaz ve depolamaz, ancak imza daha sonra eklenebilmesi için dosyada yer ayırır.

Örneğin, kullanarak `-delaysign+` bir kuruluştaki geliştirici, test edicinin genel derleme önbelleği ile kaydedebilmesi ve kullanması için imzasız test sürümlerini dağıtabilir. Derlemedeki iş tamamlandığında, kuruluşun özel anahtarından sorumlu olan kişi derlemeyi tamamen imzalayabilir. Bu compartmen, kuruluşun özel anahtarının açıklanmasını koruurken tüm geliştiricilerin derlemeler üzerinde çalışmasına izin verir.

Bir derlemeyi imzalama hakkında daha fazla bilgi için bkz. [Strong-Named derlemeleri oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) .

### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a>Visual Studio tümleşik geliştirme ortamında Set-delaysign

1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın.

2. **İmzalama** sekmesine tıklayın.

3. Değeri **yalnızca gecikmeli imzala** kutusunda ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [-keyfile](keyfile.md)
- [-keycontainer](keycontainer.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
