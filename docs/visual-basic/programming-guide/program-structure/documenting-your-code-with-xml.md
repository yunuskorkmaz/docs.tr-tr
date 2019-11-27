---
title: XML ile Kodunuzu Belgeleme
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: bdf0da7a8acc919e4a1d66b81e30c9ed912dd321
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347448"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>XML ile Kodunuzu Belgeleme (Visual Basic)

Visual Basic, kodunuzu XML kullanarak belgeedebilirsiniz

## <a name="xml-documentation-comments"></a>XML Belgeleri Yorumları

Visual Basic, projeler için otomatik olarak XML belgelerinin oluşturulması için kolay bir yol sağlar. Türleriniz ve üyelerinize yönelik otomatik olarak bir XML iskelet oluşturabilir, ardından her bir parametre için özetler, açıklayıcı belgeler ve diğer açıklamalar sağlayabilirsiniz. Uygun kurulumla, XML belgeleri projeniz ve. xml uzantısı ile aynı ada sahip bir XML dosyasına otomatik olarak yayılır. Daha fazla bilgi için bkz. [-doc](../../../visual-basic/reference/command-line-compiler/doc.md).

XML dosyası, XML olarak tüketilebilir veya başka bir şekilde yönetilebilir. Bu dosya, projenizin output. exe veya. dll dosyası ile aynı dizinde bulunur.

XML belgeleri `'''`başlar. Bu yorumların işlenmesinde bazı kısıtlamalar vardır:

- Belgeler düzgün biçimlendirilmiş XML olmalıdır. XML düzgün biçimlendirilmediyse bir uyarı oluşturulur ve belge dosyası bir hata ile karşılaşıldığını söyleyen bir açıklama içerir.

- Geliştiriciler kendi etiket kümesini oluşturmak ücretsizdir. Önerilen bir etiket kümesi vardır (Bu konudaki "Ilgili bölümler" bölümüne bakın). Önerilen etiketlerden bazılarının özel anlamları vardır:

  - Parametreleri anlatmak için \<param > etiketi kullanılır. Kullanıldıysa, derleyici parametrenin var olduğunu ve tüm parametrelerin belgelerde açıklananlandığından emin olur. Doğrulama başarısız olursa, derleyici bir uyarı verir.

  - `cref` özniteliği, bir kod öğesine başvuru sağlamak için herhangi bir etikete iliştirilebilir. Derleyici bu kod öğesinin varolduğunu doğrular. Doğrulama başarısız olursa, derleyici bir uyarı verir. Derleyici Ayrıca, `cref` özniteliğinde açıklanan bir tür ararken tüm `Imports` deyimlerine uyar.

  - \<Summary > etiketi, Visual Studio 'da IntelliSense tarafından bir tür veya üyeyle ilgili ek bilgileri göstermek için kullanılır.

## <a name="related-sections"></a>İlgili Bölümler

Belge açıklamalarıyla bir XML dosyası oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)

- [XML Dosyasını İşleme](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [Nasıl yapılır: XML Belgesi Oluşturma](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [Visual Studio'daki XML Araçları](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic ile uygulama geliştirme](../../../visual-basic/developing-apps/index.md)
- [Visual Basic programlama kılavuzu](../../../visual-basic/programming-guide/index.md)
