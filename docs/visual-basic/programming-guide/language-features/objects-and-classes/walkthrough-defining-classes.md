---
title: Sınıflar (Visual Basic) tanımlama
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
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43403548"
---
# <a name="walkthrough-defining-classes-visual-basic"></a>İzlenecek Yol: Sınıfları Tanımlama (Visual Basic)

Bu yönerge, ardından nesneleri oluşturmak için kullanabileceğiniz sınıflarını tanımlamak nasıl gösterir. Ayrıca yeni sınıfa özellikler ve yöntemler eklemek nasıl gösterir ve bir nesneyi başlatmaya gösterilmektedir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>Bir sınıf tanımlamak için
  
1.  Tıklayarak bir proje oluşturun **yeni proje** üzerinde **dosya** menüsü. **Yeni proje** iletişim kutusu görüntülenir.  
  
2.  Windows uygulamasını yeni proje görüntülemek için Visual Basic proje şablonları listesinden seçin.  
  
3.  Tıklayarak, projeye yeni bir sınıf ekleyin **sınıfı Ekle** üzerinde **proje** menüsü. **Yeni Öğe Ekle** iletişim kutusu görüntülenir.  
  
4.  Seçin **sınıfı** şablonu.  
  
5.  Yeni bir sınıf adı `UserNameInfo.vb`ve ardından **Ekle** yeni sınıfı seçerek kodu görüntüleyin.  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    >  Visual Basic kullanabileceğiniz **Kod Düzenleyicisi** yazarak başlangıç formunuza bir sınıf eklemek için `Class` anahtar ardından yeni sınıfın adı. **Kod Düzenleyicisi** karşılık gelen sağlar `End Class` deyimi sizin için.  
  
6.  Arasına aşağıdaki kodu ekleyerek sınıfı için özel bir alan tanımlayın `Class` ve `End Class` ifadeleri:  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     Alan olarak bildirme `Private` yalnızca sınıf kullanılabileceği anlamına gelir. Erişim değiştiricileri gibi kullanarak, alanlar bir sınıfın dışında kullanılabilir yapabilirsiniz `Public` daha fazla erişim sağlar. Daha fazla bilgi için [erişim düzeyini Visual Basic'te](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7.  Aşağıdaki kodu ekleyerek sınıfı için bir özellik tanımlayın:  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8.  Sınıfı için bir yöntem aşağıdaki kodu ekleyerek tanımlayın:  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. Adlı bir yordam ekleyerek yeni bir sınıf için parametreli bir kurucu tanımlamak `Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     `Sub New` Oluşturucusu bu sınıfına göre bir nesne oluşturulduğunda otomatik olarak çağrılır. Bu oluşturucu, kullanıcı adını tutan bir alanın değerini ayarlar.  
  
## <a name="to-create-a-button-to-test-the-class"></a>Test sınıfı için bir düğme oluşturmak için
  
1.  Başlangıç formu adına tıklanarak tasarım moduna değiştirin **Çözüm Gezgini** tıklayıp **Görünüm Tasarımcısı**. Varsayılan olarak, Windows Uygulama projeleri için başlangıç formu Form1.vb olan. Ana formu sonra görünür.  
  
2.  Ana forma bir düğme ekleyin ve kodunu görüntülemek için çift tıklayın `Button1_Click` olay işleyicisi. Test yordamı çağırmak için aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>Uygulamanızı çalıştırmak için
  
1.  F5 tuşuna basarak uygulamanızı çalıştırın. Formdaki test yordamı çağırmak için düğmeye tıklayın. Özgün belirten bir ileti görüntüler `UserName` yordamı adında "MOORE, BOBBY", çünkü `Capitalize` nesnesinin yöntemi.  
  
2.  Tıklayın **Tamam** ileti kutusunu kapatın. `Button1 Click` Yordam değerini değiştirir `UserName` özelliği ve yeni değeri belirten bir ileti görüntüler `UserName` "Worden, ALi" olduğu.  
  
## <a name="see-also"></a>Ayrıca bkz.

[Nesne odaklı programlama (Visual Basic)](../../concepts/object-oriented-programming.md)  
[Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)