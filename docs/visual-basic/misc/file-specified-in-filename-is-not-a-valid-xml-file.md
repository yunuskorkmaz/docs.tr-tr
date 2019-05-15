---
title: Dosya adında belirtilen dosya geçerli bir XML dosyası değil.
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: 1615722d19e1a24ee4e72bc702dbce3fe30411a4
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592896"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>Dosya adında belirtilen dosya geçerli bir XML dosyası değil.

Girdiğiniz dosya adı geçerli bir XML dosyası değil. İzin verilen yapısı ve bir XML belgesinin içeriğini belirtmek için bir belge türü tanımı (DTD'nin), Microsoft XML verileri azaltılmış (XDR) şema veya bir XML Şeması Tanım Dili (XSD) şemaya kullanabilirsiniz. XSD şemaları, .NET Framework XML dilbilgisi belirtmek için tercih edilen yoludur.

> [!NOTE]
> Visual Studio'nun önceki bazı sürümlerinde **XML Tasarımcısı** türü belirtilmiş veri kümeleri ve XML şema Tasarımcısı. **XML Tasarımcısı** XML şema dosyalarını oluşturmak ve düzenlemek için hala kullanılabilir. Ancak, Visual Studio 2012'de, oluşturma ve düzenleme türü belirtilmiş datasets için tasarımcı olan **veri kümesi Tasarımcısı**. Daha fazla bilgi için [oluşturma ve yazılan veri kümelerini düzenleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Doğru dosya adı sağlayarak denetleyin.

- Belirtilen dosya içine kontrol etmek istediğiniz XML dosyası yükleyerek geçerli XML içerdiğinden denetleyin **XML Tasarımcısı**. Gelen **XML** menüsünü tıklatın **doğrulamak XML**. Hatalar görüntülenir **görev listesi**.

- XML dosyası ilişkili bir XML şeması varsa, öğeleri tanımlanmış bir yapı içinde görünür ve tek tek öğelerine içeriğini belirtilen şemada bildirilen veri türleri için uygun olduğunu denetleyin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml>
- [Nasıl yapılır: Dosya yollarını ayrıştırma](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
