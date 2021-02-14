---
description: 'Hakkında daha fazla bilgi edinin: kodunuzu XML ile belgeleme (Visual Basic)'
title: XML ile Kodunuzu Belgeleme
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: b554007bdd5183d0d92dc7ff62d08885f4b7f486
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476013"
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

- [Visual Studio 'da XML araçları](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic ile Uygulama Geliştirme](../../developing-apps/index.md)
- [Visual Basic Programlama Kılavuzu](../index.md)
