---
title: XML ile Kodunuzu Belgeleme (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 645dd4a8a9d1c78fd54f0f31ad0efd772b671d39
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>XML ile Kodunuzu Belgeleme (Visual Basic)
Visual Basic'te XML kullanarak kodunuzu belgeleme  
  
## <a name="xml-documentation-comments"></a>XML Belgeleri Yorumları  
 Visual Basic projeleri için XML belgeleri otomatik olarak oluşturmak için kolay bir yol sağlar. Bir XML çatıyı türleri ve üyeleri için otomatik olarak oluşturmak ve ardından her bir parametreyi ve diğer açıklamalar için özetleri, açıklayıcı belgeleri sağlayın. Uygun Kurulum'a XML belgeleri otomatik olarak projeniz ve .xml uzantısına aynı ada sahip bir XML dosyasına yayınlanır. Daha fazla bilgi için bkz: [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
 XML dosyasını tüketilen veya aksi halde XML olarak yönetilebilir. Bu dosya, projenizin çıktı .exe veya .dll dosyası ile aynı dizinde bulunur.  
  
 XML belgeleri ile başlayan `'''`. Bu açıklamalar işlenmesini bazı kısıtlamaları vardır:  
  
-   Belge doğru biçimlendirilmiş XML. XML doğru biçimlendirilmemiş, bir uyarı oluşturulur ve bir hatayla karşılaşıldı belirten bir açıklama belge dosyası içerir.  
  
-   Geliştiriciler kendi etiketleri kümesi oluşturmak boş. Önerilen etiketler ("İlgili bölümler" konusuna bakın) birtakım yoktur. Önerilen etiketler bazıları özel anlamlara sahiptir:  
  
    -   \<Param > etiketi parametrelerini tanımlamak için kullanılır. Kullandıysanız, derleyici parametresi var olduğundan ve tüm parametreleri belgelerinde açıklanan doğrulayın. Doğrulama başarısız olursa, derleyici bir uyarı verir.  
  
    -   `cref` Öznitelik, bir başvuru code öğesi sağlamak için herhangi bir etiket için eklenebilir. Derleyici, bu kod öğesi var olduğunu doğrular. Doğrulama başarısız olursa, derleyici bir uyarı verir. Derleyici de herhangi uyar `Imports` içinde tanımlanan bir tür ararken deyimleri `cref` özniteliği.  
  
    -   \<Özet > etiketi IntelliSense içinde tarafından kullanılan [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] bir tür veya üye hakkında ek bilgi görüntülemek için.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Belge açıklamaları bir XML dosyası oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [XML Dosyasını İşleme](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [Nasıl yapılır: XML Belgesi Oluşturma](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [Visual Studio'daki XML Araçları](/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic ile uygulamaları geliştirme](../../../visual-basic/developing-apps/index.md)  
 [Visual Basic programlama kılavuzu](../../../visual-basic/programming-guide/index.md)
