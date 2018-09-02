---
title: XML ile Kodunuzu Belgeleme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: b99c37f30d595e114bb4625a2881a9f0b463f5e6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405185"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>XML ile Kodunuzu Belgeleme (Visual Basic)
Visual Basic'te XML kullanarak kodunuzu belgeleme  
  
## <a name="xml-documentation-comments"></a>XML Belgeleri Yorumları  
 Visual Basic projeleri için XML belgeleri otomatik olarak oluşturmak için kolay bir yol sağlar. Bir XML skeleton türler ve üyeler için otomatik olarak oluşturmak ve özetleri, açıklayıcı belgeleri her parametre ve diğer açıklamalar sağlar. Uygun Kurulum, XML belgeleri projenizi ve .xml uzantısı olarak aynı ada sahip bir XML dosyasına otomatik olarak yayılır. Daha fazla bilgi için [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
 XML dosyası kullanılan veya aksi halde XML olarak yönetilebilir. Bu dosya, projenizin çıkış .exe veya .dll dosyası ile aynı dizinde bulunur.  
  
 XML belgeleri ile başlayan `'''`. Bu açıklamalar işlenmesini bazı kısıtlamalar mevcuttur:  
  
-   Belgeler doğru biçimlendirilmiş XML. XML düzgün biçimlendirilmemiş ise bir uyarı oluşturulur ve belge dosyası bir hatayla karşılaşıldı belirten bir açıklama içerir.  
  
-   Geliştiriciler kendi kümesi etiketleri oluşturmak ücretsizdir. Önerilen etiketler ("İlgili bölümler" bölümüne bakın) kümesi yok. Önerilen etiketler bazıları, özel anlamları vardır:  
  
    -   \<Param > etiketi, parametreler tanımlamak için kullanılır. Kullandıysanız, derleyici parametresi var olduğundan ve tüm parametreleri belgelerinde açıklanan doğrulayın. Doğrulama başarısız olursa, derleyici bir uyarı verir.  
  
    -   `cref` Öznitelik, bir kod öğesi başvuru sağlamak için herhangi bir etiket eklenebilir. Derleyici, bu kod öğesi var olduğunu doğrular. Doğrulama başarısız olursa, derleyici bir uyarı verir. Derleyici ayrıca tüm uyar `Imports` içinde tanımlanan bir tür ararken deyimleri `cref` özniteliği.  
  
    -   \<Özet > etiketi Visual Studio IntelliSense tarafından bir tür veya üyeyle ilgili ek bilgileri görüntülemek için kullanılır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Belge açıklamaları bir XML dosyası oluşturma hakkında daha fazla bilgi edinmek için aşağıdaki konulara bakın:  
  
-   [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)  
  
-   [XML Dosyasını İşleme](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [Nasıl yapılır: XML Belgesi Oluşturma](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [Visual Studio'daki XML Araçları](/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic ile uygulama geliştirme](../../../visual-basic/developing-apps/index.md)  
 [Visual Basic programlama kılavuzu](../../../visual-basic/programming-guide/index.md)
