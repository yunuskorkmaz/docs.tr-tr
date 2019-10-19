---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 3ee94df096b756be544964cfbbd405355e3f728f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581268"
---
# <a name="-delaysign"></a>-delaysign

Derlemenin tamamen veya kısmen imzalanacağını belirtir.

## <a name="syntax"></a>Sözdizimi

```console
-delaysign[+ | -]
```

## <a name="arguments"></a>Arguments

`+` &#124; `-`  
İsteğe bağlı. Tam olarak imzalanan bir derleme istiyorsanız `-delaysign-` kullanın. Ortak anahtarı derlemeye koymak ve imzalı karma için alan ayırmak istiyorsanız `-delaysign+` kullanın. Varsayılan, `-delaysign-` değeridir.

## <a name="remarks"></a>Açıklamalar

[-Keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) veya [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)ile kullanılmamışsa `-delaysign` seçeneğinin hiçbir etkisi yoktur.

Tam olarak imzalanan bir derleme istediğinizde, derleyici bildirimi içeren dosyayı (derleme meta verileri) karma hale getirir ve bu karmayı özel anahtarla imzalar. Elde edilen dijital imza, bildirimi içeren dosyada depolanır. Bir derlemenin gecikmesi gecikmeli olduğunda, derleyici imzayı hesaplamaz ve depolamaz, ancak imza daha sonra eklenebilmesi için dosyada yer ayırır.

Örneğin, `-delaysign+` ' ı kullanarak bir kuruluştaki geliştirici, test edicinin genel derleme önbelleği ile kaydedebilmesi ve kullanması için imzasız test sürümlerini dağıtabilir. Derlemedeki iş tamamlandığında, kuruluşun özel anahtarından sorumlu olan kişi derlemeyi tamamen imzalayabilir. Bu compartmen, kuruluşun özel anahtarının açıklanmasını koruurken tüm geliştiricilerin derlemeler üzerinde çalışmasına izin verir.

Bir derlemeyi imzalama hakkında daha fazla bilgi için bkz. [tanımlayıcı adlı derlemeler oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) .

### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a>Visual Studio tümleşik geliştirme ortamında Set-delaysign

1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın.

2. **İmzalama** sekmesine tıklayın.

3. Değeri **yalnızca gecikmeli imzala** kutusunda ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
