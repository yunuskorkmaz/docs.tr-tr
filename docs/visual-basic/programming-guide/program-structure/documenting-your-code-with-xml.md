---
title: XML ile Kodunuzu Belgeleme
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: f391fb909cfe4de8f27afb24d6db389e2c8cdfae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590935"
---
# <a name="document-your-code-with-xml-visual-basic"></a>Kodunuzu XML ile belgeleyin (Visual Basic)

Visual Basic, kodunuzu XML kullanarak belgeedebilirsiniz.

## <a name="xml-documentation-comments"></a>XML belgeleri yorumları

Visual Basic, projeler için otomatik olarak XML belgelerinin oluşturulması için kolay bir yol sağlar. Türleriniz ve üyelerinize yönelik otomatik olarak bir XML iskelet oluşturabilir, ardından her bir parametre için özetler, açıklayıcı belgeler ve diğer açıklamalar sağlayabilirsiniz. Uygun kurulumla, XML belgeleri projenizle aynı kök dosya adına sahip bir XML dosyasına otomatik olarak yayılır. Daha fazla bilgi için bkz. [-doc](../../reference/command-line-compiler/doc.md).

XML dosyası, XML olarak tüketilebilir veya başka bir şekilde yönetilebilir. Bu dosya, projenizin output. exe veya. dll dosyası ile aynı dizinde bulunur.

XML belgeleri ile başlar `'''` . Bu yorumların işlenmesinde bazı kısıtlamalar vardır:

- Belgeler düzgün biçimlendirilmiş XML olmalıdır. XML düzgün biçimlendirilmediyse bir uyarı oluşturulur ve belge dosyası bir hata ile karşılaşıldığını söyleyen bir açıklama içerir.

- Geliştiriciler kendi etiket kümesini oluşturmak ücretsizdir. Önerilen bir etiket kümesi vardır (bkz. [XML açıklama etiketleri](../../language-reference/xmldoc/index.md)). Önerilen etiketlerden bazılarının özel anlamları vardır:

  - \<param>Etiketi, parametreleri tanımlamakta kullanılır. Kullanıldıysa, derleyici parametrenin var olduğunu ve tüm parametrelerin belgelerde açıklananlandığından emin olur. Doğrulama başarısız olursa, derleyici bir uyarı verir.

  - `cref`Özniteliği bir kod öğesine başvuru sağlamak için herhangi bir etikete iliştirilebilir. Derleyici bu kod öğesinin varolduğunu doğrular. Doğrulama başarısız olursa, derleyici bir uyarı verir. Derleyici, `Imports` özniteliğinde açıklanan bir tür ararken de herhangi bir deyime uyar `cref` .

  - \<summary>Etiketi, Visual Studio 'Da IntelliSense tarafından bir tür veya üyeyle ilgili ek bilgileri göstermek için kullanılır.

## <a name="related-sections"></a>İlgili bölümler

Belge açıklamalarıyla bir XML dosyası oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [-doc](../../reference/command-line-compiler/doc.md)

- [XML Açıklama Etiketleri](../../language-reference/xmldoc/index.md)

- [XML dosyası işleniyor](processing-the-xml-file.md)

- [Nasıl yapılır: XML Belgesi Oluşturma](how-to-create-xml-documentation.md)

- [Visual Studio'daki XML Araçları](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic ile Uygulama Geliştirme](../../developing-apps/index.md)
- [Visual Basic Programlama Kılavuzu](../index.md)
