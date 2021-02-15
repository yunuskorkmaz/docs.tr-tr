---
description: 'Hakkında daha fazla bilgi edinin: dosya adı içinde belirtilen dosya geçerli bir XML dosyası değil'
title: Dosya adında belirtilen dosya geçerli bir XML dosyası değil
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: c7d521986f3489345117a3947ed1e9b459af897e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472988"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>Dosya adında belirtilen dosya geçerli bir XML dosyası değil

Sağladığınız dosya adı geçerli bir XML dosyası değil. Bir XML belgesinin izin verilen yapısını ve içeriğini belirtmek için bir belge türü tanımı (DTD), Microsoft XML-Data azaltılmış (XDR) şeması veya bir XML şeması tanım dili (XSD) şeması kullanabilirsiniz. XSD şemaları, .NET Framework XML dilbilgisi belirtmek için tercih edilen yoldur.

> [!NOTE]
> Visual Studio 'nun bazı önceki sürümlerinde **XML Designer** , türü belirtilmiş veri KÜMELERI ve XML şeması için tasarımcı olur. XML **Designer** , XML şema dosyalarını oluşturmak ve düzenlemek için hala kullanılabilir. Ancak, Visual Studio 2012 ' de, yazılan veri kümelerini oluşturma ve düzenlemeyle ilgili tasarımcı **veri kümesi Tasarımcısı**. Daha fazla bilgi için bkz. [türü belirtilmiş veri kümeleri oluşturma ve düzenlemeyle](/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Doğru dosya adını tedarik edin.

- **XML tasarımcısına** denetlemek istediğiniz XML dosyasını yükleyerek, belirtilen DOSYANıN geçerli XML içerdiğinden emin olun. **XML** menüsünde **XML 'yi doğrula**' ya tıklayın. Hatalar **görev listesi** görüntülenir.

- XML dosyasında ilişkili bir XML şeması varsa, öğelerin tanımlanan yapıda göründüğünden ve tek tek öğelerin içeriğinin şemada belirtilen tanımlanmış veri türlerine uygun olduğundan emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml>
- [Nasıl yapılır: Dosya Yollarını Ayrıştırma](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
