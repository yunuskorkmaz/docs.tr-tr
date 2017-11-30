---
title: "Tanımlayan sınıflar (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- execution [Visual Basic], ending
- objects [Visual Basic], initializing
- Initialize event [Visual Basic]
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ec002e1709fa5fe31dfe7744fb91a230c32337a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-defining-classes-visual-basic"></a>İzlenecek Yol: Sınıfları Tanımlama (Visual Basic)
Bu kılavuz, ardından nesneleri oluşturmak için kullanabileceğiniz sınıflarını tanımlamak gösterilmiştir. Ayrıca özellikleri ve yöntemleri yeni sınıfa eklemeyi gösterir ve bir nesneyi başlatmak gösterilmiştir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-define-a-class"></a>Bir sınıf tanımlamak için  
  
1.  Bir proje oluşturun **yeni proje** üzerinde **dosya** menüsü. **Yeni proje** iletişim kutusu görüntülenir.  
  
2.  Windows uygulama listesinden seçin [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] proje şablonlarını yeni proje görüntülemek için.  
  
3.  Projeye tıklayarak yeni bir sınıf ekleyin **sınıfı Ekle** üzerinde **proje** menüsü. **Yeni Öğe Ekle** iletişim kutusu görüntülenir.  
  
4.  Seçin **sınıfı** şablonu.  
  
5.  Yeni sınıf `UserNameInfo.vb`ve ardından **Ekle** yeni sınıf kodunu görüntülemek için.  
  
     [!code-vb[VbVbalrOOP#5](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]  
  
    > [!NOTE]
    >  Kullanabileceğiniz [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] **Kod düzenleyicisinde** yazarak başlangıç formunuz için bir sınıf eklemek için `Class` anahtar sözcüğü ardından yeni sınıfın adı. **Kod düzenleyicisinde** karşılık gelen sağlar `End Class` sizin için deyimi.  
  
6.  Aşağıdaki kod arasında ekleyerek sınıfı için özel bir alan tanımlayın `Class` ve `End Class` deyimleri:  
  
     [!code-vb[VbVbalrOOP#7](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]  
  
     Alan olarak bildirme `Private` yalnızca sınıfında kullanılabileceği anlamına gelir. Erişim değiştiricileri gibi kullanarak, alanları sınıf dışındaki kullanılabilir yapabilirsiniz `Public` daha fazla erişim sağlar. Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7.  Bir özellik sınıfı için aşağıdaki kodu ekleyerek tanımlayın:  
  
     [!code-vb[VbVbalrOOP#8](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]  
  
8.  Sınıfı için bir yöntem, aşağıdaki kodu ekleyerek tanımlayın:  
  
     [!code-vb[VbVbalrOOP#9](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]  
  
9. Adlı bir yordam ekleyerek yeni sınıfı için parametreli bir oluşturucu tanımlarsınız `Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]  
  
     `Sub New` Oluşturucusu bu sınıfına dayalı bir nesne oluşturulduğunda otomatik olarak çağrılır. Bu oluşturucu kullanıcı adı tutan alanın değerini ayarlar.  
  
### <a name="to-create-a-button-to-test-the-class"></a>Sınıfı test etmek için bir düğme oluşturmak için  
  
1.  Başlangıç formu tasarım adını sağ tıklayarak moduna **Çözüm Gezgini** ve ardından **Görünüm Tasarımcısı**. Varsayılan olarak, Windows uygulaması projeleri için başlangıç formu Form1.vb olarak adlandırılır. Ana form sonra görünür.  
  
2.  Kodunu görüntülemek için çift tıklayın ve ana forma düğme ekleme `Button1_Click` olay işleyicisi. Test yordam çağrısı için aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbalrOOP#12](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]  
  
### <a name="to-run-your-application"></a>Uygulamanızı çalıştırmak için  
  
1.  F5 tuşuna basarak uygulamanızı çalıştırın. Test yordam çağrısı forma düğmesine tıklayın. Özgün belirten bir ileti görüntüler `UserName` yordamı adında "MOORE, BOBBY", çünkü `Capitalize` nesnesinin yöntemi.  
  
2.  Tıklatın **Tamam** ileti kutusu kapatılamadı. `Button1 Click` Yordam değerini değiştirir `UserName` özelliği ve yeni değeri belirten bir ileti görüntüler `UserName` "Worden, Can" değil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nesne odaklı programlama](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)  
 [Nesneler ve sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
