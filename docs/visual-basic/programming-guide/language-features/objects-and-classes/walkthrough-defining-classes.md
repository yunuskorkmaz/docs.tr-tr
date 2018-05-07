---
title: Tanımlayan sınıflar (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: aac30a8b0272ae6c141138a91585953237ab8098
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-defining-classes-visual-basic"></a>İzlenecek Yol: Sınıfları Tanımlama (Visual Basic)

Bu kılavuz, ardından nesneleri oluşturmak için kullanabileceğiniz sınıflarını tanımlamak gösterilmiştir. Ayrıca özellikleri ve yöntemleri yeni sınıfa eklemeyi gösterir ve bir nesneyi başlatmak gösterilmiştir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>Bir sınıf tanımlamak için
  
1.  Bir proje oluşturun **yeni proje** üzerinde **dosya** menüsü. **Yeni proje** iletişim kutusu görüntülenir.  
  
2.  Windows uygulaması yeni proje görüntülemek için Visual Basic proje şablonları listesinden seçin.  
  
3.  Projeye tıklayarak yeni bir sınıf ekleyin **sınıfı Ekle** üzerinde **proje** menüsü. **Yeni Öğe Ekle** iletişim kutusu görüntülenir.  
  
4.  Seçin **sınıfı** şablonu.  
  
5.  Yeni sınıf `UserNameInfo.vb`ve ardından **Ekle** yeni sınıf kodunu görüntülemek için.  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    >  Visual Basic kullanabilirsiniz **Kod düzenleyicisinde** yazarak başlangıç formunuz için bir sınıf eklemek için `Class` anahtar sözcüğü ardından yeni sınıfın adı. **Kod düzenleyicisinde** karşılık gelen sağlar `End Class` sizin için deyimi.  
  
6.  Aşağıdaki kod arasında ekleyerek sınıfı için özel bir alan tanımlayın `Class` ve `End Class` deyimleri:  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     Alan olarak bildirme `Private` yalnızca sınıfında kullanılabileceği anlamına gelir. Erişim değiştiricileri gibi kullanarak, alanları sınıf dışındaki kullanılabilir yapabilirsiniz `Public` daha fazla erişim sağlar. Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7.  Bir özellik sınıfı için aşağıdaki kodu ekleyerek tanımlayın:  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8.  Sınıfı için bir yöntem, aşağıdaki kodu ekleyerek tanımlayın:  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. Adlı bir yordam ekleyerek yeni sınıfı için parametreli bir oluşturucu tanımlarsınız `Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     `Sub New` Oluşturucusu bu sınıfına dayalı bir nesne oluşturulduğunda otomatik olarak çağrılır. Bu oluşturucu kullanıcı adı tutan alanın değerini ayarlar.  
  
## <a name="to-create-a-button-to-test-the-class"></a>Sınıfı test etmek için bir düğme oluşturmak için
  
1.  Başlangıç formu tasarım adını sağ tıklayarak moduna **Çözüm Gezgini** ve ardından **Görünüm Tasarımcısı**. Varsayılan olarak, Windows uygulaması projeleri için başlangıç formu Form1.vb olarak adlandırılır. Ana form sonra görünür.  
  
2.  Kodunu görüntülemek için çift tıklayın ve ana forma düğme ekleme `Button1_Click` olay işleyicisi. Test yordam çağrısı için aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>Uygulamanızı çalıştırmak için
  
1.  F5 tuşuna basarak uygulamanızı çalıştırın. Test yordam çağrısı forma düğmesine tıklayın. Özgün belirten bir ileti görüntüler `UserName` yordamı adında "MOORE, BOBBY", çünkü `Capitalize` nesnesinin yöntemi.  
  
2.  Tıklatın **Tamam** ileti kutusu kapatılamadı. `Button1 Click` Yordam değerini değiştirir `UserName` özelliği ve yeni değeri belirten bir ileti görüntüler `UserName` "Worden, Can" değil.  
  
## <a name="see-also"></a>Ayrıca bkz.

[Nesne odaklı programlama (Visual Basic)](../../concepts/object-oriented-programming.md)  
[Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)