---
title: Sınıfları tanımlama (Visual Basic)
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
ms.openlocfilehash: 679f4fd55f142c2c4bb63a556feb95c074960b12
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914728"
---
# <a name="walkthrough-defining-classes-visual-basic"></a>İzlenecek yol: Sınıfları tanımlama (Visual Basic)

Bu izlenecek yolda, daha sonra nesneleri oluşturmak için kullanabileceğiniz sınıfların nasıl tanımlanacağı gösterilmektedir. Ayrıca, yeni sınıfa nasıl özellik ve Yöntem ekleneceğini ve bir nesnenin nasıl başlatılacağını gösterir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>Bir sınıf tanımlamak için
  
1. **Dosya** menüsünde **Yeni proje ' ye** tıklayarak bir proje oluşturun. **Yeni Proje** iletişim kutusu görünür.  
  
2. Yeni projeyi göstermek için Visual Basic proje şablonları listesinden Windows uygulaması ' nı seçin.  
  
3. **Proje** menüsünde **Sınıf Ekle** ' ye tıklayarak projeye yeni bir sınıf ekleyin. **Yeni Öğe Ekle** iletişim kutusu görünür.  
  
4. **Sınıf** şablonunu seçin.  
  
5. Yeni `UserNameInfo.vb`sınıfı adlandırın ve ardından **Ekle** ' ye tıklayarak yeni sınıf için kodu görüntüleyin.  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    > `Class` Anahtar sözcüğünü ve ardından yeni sınıfın adını yazarak başlangıç formunuza bir sınıf eklemek için Visual Basic **kod düzenleyicisini** kullanabilirsiniz. **Kod Düzenleyicisi** sizin için karşılık gelen `End Class` bir bildirim sağlar.  
  
6. `Class` Ve`End Class` deyimleri arasına aşağıdaki kodu ekleyerek sınıf için özel bir alan tanımlayın:  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     Alanı olarak `Private` bildirmek, yalnızca sınıfında kullanılabileceği anlamına gelir. Daha fazla erişim sağlayan gibi `Public` erişim değiştiricilerini kullanarak alanları bir sınıfın dışından kullanılabilir hale getirebilirsiniz. Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7. Aşağıdaki kodu ekleyerek sınıf için bir özellik tanımlayın:  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. Aşağıdaki kodu ekleyerek sınıf için bir yöntem tanımlayın:  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. Adlı `Sub New`bir yordam ekleyerek yeni sınıf için parametreli bir Oluşturucu tanımlayın:  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     Bu sınıfa dayalı bir nesne oluşturulduğunda Oluşturucuotomatikolarakçağrılır.`Sub New` Bu Oluşturucu, Kullanıcı adını tutan alanın değerini ayarlar.  
  
## <a name="to-create-a-button-to-test-the-class"></a>Sınıfı test etmek üzere bir düğme oluşturmak için
  
1. Başlangıç formunu, **Çözüm Gezgini** adına sağ tıklayıp **Görünüm Tasarımcısı**' na tıklayarak tasarım moduna değiştirin. Varsayılan olarak, Windows uygulama projeleri için başlangıç formu Form1. vb olarak adlandırılır. Ana form daha sonra görüntülenir.  
  
2. Ana forma bir düğme ekleyin ve `Button1_Click` olay işleyicisi için kodu göstermek üzere çift tıklayın. Test yordamını çağırmak için aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>Uygulamanızı çalıştırmak için
  
1. F5 tuşuna basarak uygulamanızı çalıştırın. Test yordamını çağırmak için formdaki düğmeye tıklayın. Bu, yordamın nesne `UserName` `Capitalize` yöntemi olarak adlandırıldığından, orijinalin "Moore, bodire" olduğunu belirten bir ileti görüntüler.  
  
2. İleti kutusunu kapatmak için **Tamam** ' ı tıklatın. Yordam, `UserName` özelliğinin değerini değiştirir ve yeni değerinin `UserName` "Worden, ali" olduğunu belirten bir ileti görüntüler. `Button1 Click`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne odaklı programlama (Visual Basic)](../../concepts/object-oriented-programming.md)
- [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
