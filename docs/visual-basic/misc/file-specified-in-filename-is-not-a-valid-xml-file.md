---
title: Dosya adında belirtilen dosya geçerli bir XML dosyası değil
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: a84042490935e3e7e5a6de2a802d9effd5b4d3d4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358354"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>Dosya adında belirtilen dosya geçerli bir XML dosyası değil

Sağladığınız dosya adı geçerli bir XML dosyası değil. Bir XML belgesinin izin verilen yapısını ve içeriğini belirtmek için bir belge türü tanımı (DTD), Microsoft XML verileri azaltılmış (XDR) şeması veya bir XML şeması tanım dili (XSD) şeması kullanabilirsiniz. XSD şemaları, .NET Framework XML dilbilgisi belirtmek için tercih edilen yoldur.

> [!NOTE]
> Visual Studio 'nun bazı önceki sürümlerinde **XML Designer** , türü belirtilmiş veri KÜMELERI ve XML şeması için tasarımcı olur. XML **Designer** , XML şema dosyalarını oluşturmak ve düzenlemek için hala kullanılabilir. Ancak, Visual Studio 2012 ' de, yazılan veri kümelerini oluşturma ve düzenlemeyle ilgili tasarımcı **veri kümesi Tasarımcısı**. Daha fazla bilgi için bkz. [türü belirtilmiş veri kümeleri oluşturma ve düzenlemeyle](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Doğru dosya adını tedarik edin.

- **XML tasarımcısına**denetlemek istediğiniz XML dosyasını yükleyerek, belirtilen DOSYANıN geçerli XML içerdiğinden emin olun. **XML** menüsünde **XML 'yi doğrula**' ya tıklayın. Hatalar **görev listesi**görüntülenir.

- XML dosyasında ilişkili bir XML şeması varsa, öğelerin tanımlanan yapıda göründüğünden ve tek tek öğelerin içeriğinin şemada belirtilen tanımlanmış veri türlerine uygun olduğundan emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml>
- [Nasıl yapılır: Dosya Yollarını Ayrıştırma](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
