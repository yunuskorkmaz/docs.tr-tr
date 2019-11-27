---
title: Sınıfları Tanımlama
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
ms.openlocfilehash: bd3f6e5cff41551240d9904ab93af8758eb104d2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346084"
---
# <a name="walkthrough-defining-classes-visual-basic"></a>İzlenecek Yol: Sınıfları Tanımlama (Visual Basic)

Bu izlenecek yolda, daha sonra nesneleri oluşturmak için kullanabileceğiniz sınıfların nasıl tanımlanacağı gösterilmektedir. Ayrıca, yeni sınıfa nasıl özellik ve Yöntem ekleneceğini ve bir nesnenin nasıl başlatılacağını gösterir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>Bir sınıf tanımlamak için
  
1. **Dosya** menüsünde **Yeni proje ' ye** tıklayarak bir proje oluşturun. **Yeni proje** iletişim kutusu görüntülenir.  
  
2. Yeni projeyi göstermek için Visual Basic proje şablonları listesinden Windows uygulaması ' nı seçin.  
  
3. **Proje** menüsünde **Sınıf Ekle** ' ye tıklayarak projeye yeni bir sınıf ekleyin. **Yeni öğe Ekle** iletişim kutusu görüntülenir.  
  
4. **Sınıf** şablonunu seçin.  
  
5. Yeni sınıf `UserNameInfo.vb`adlandırın ve ardından **Ekle** ' ye tıklayarak yeni sınıf için kodu görüntüleyin.  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    > Visual Basic **kod düzenleyicisini** kullanarak başlangıç formunuza bir sınıf ekleyebilirsiniz ve ardından yeni sınıfın adı ile `Class` anahtar sözcüğünü yazarak başlangıç formunuza bir sınıf ekleyebilirsiniz. **Kod Düzenleyicisi** sizin için karşılık gelen bir `End Class` ekstresi sağlar.  
  
6. `Class` ve `End Class` deyimleri arasına aşağıdaki kodu ekleyerek sınıf için özel bir alan tanımlayın:  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     Alanı `Private` olarak bildirmek, yalnızca sınıfında kullanılabileceği anlamına gelir. Daha fazla erişim sağlayan `Public` gibi erişim değiştiricilerini kullanarak alanları bir sınıfın dışından kullanılabilir hale getirebilirsiniz. Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7. Aşağıdaki kodu ekleyerek sınıf için bir özellik tanımlayın:  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. Aşağıdaki kodu ekleyerek sınıf için bir yöntem tanımlayın:  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. `Sub New`adlı bir yordam ekleyerek yeni sınıf için parametreli bir Oluşturucu tanımlayın:  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     `Sub New` Oluşturucusu, bu sınıfa dayalı bir nesne oluşturulduğunda otomatik olarak çağrılır. Bu Oluşturucu, Kullanıcı adını tutan alanın değerini ayarlar.  
  
## <a name="to-create-a-button-to-test-the-class"></a>Sınıfı test etmek üzere bir düğme oluşturmak için
  
1. Başlangıç formunu, **Çözüm Gezgini** adına sağ tıklayıp **Görünüm Tasarımcısı**' na tıklayarak tasarım moduna değiştirin. Varsayılan olarak, Windows uygulama projeleri için başlangıç formu Form1. vb olarak adlandırılır. Ana form daha sonra görüntülenir.  
  
2. Ana forma bir düğme ekleyin ve `Button1_Click` olay işleyicisi için kodu göstermek üzere çift tıklayın. Test yordamını çağırmak için aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>Uygulamanızı çalıştırmak için
  
1. F5 tuşuna basarak uygulamanızı çalıştırın. Test yordamını çağırmak için formdaki düğmeye tıklayın. Yordamın, nesnenin `Capitalize` yöntemini çağırdığı için, özgün `UserName` "MOORE, BODIRE" olduğunu belirten bir ileti görüntüler.  
  
2. İleti kutusunu kapatmak için **Tamam** ' ı tıklatın. `Button1 Click` yordamı `UserName` özelliğinin değerini değiştirir ve yeni `UserName` değerinin "Worden, ali" olduğunu belirten bir ileti görüntüler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne odaklı programlama (Visual Basic)](../../concepts/object-oriented-programming.md)
- [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
