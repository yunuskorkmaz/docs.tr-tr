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
ms.openlocfilehash: 646c6ce307131f3edba194af19920eade9c1753c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389120"
---
# <a name="walkthrough-defining-classes-visual-basic"></a>İzlenecek Yol: Sınıfları Tanımlama (Visual Basic)

Bu izlenecek yolda, daha sonra nesneleri oluşturmak için kullanabileceğiniz sınıfların nasıl tanımlanacağı gösterilmektedir. Ayrıca, yeni sınıfa nasıl özellik ve Yöntem ekleneceğini ve bir nesnenin nasıl başlatılacağını gösterir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>Bir sınıf tanımlamak için
  
1. **Dosya** menüsünde **Yeni proje ' ye** tıklayarak bir proje oluşturun. **Yeni Proje** iletişim kutusu görünür.  
  
2. Yeni projeyi göstermek için Visual Basic proje şablonları listesinden Windows uygulaması ' nı seçin.  
  
3. **Proje** menüsünde **Sınıf Ekle** ' ye tıklayarak projeye yeni bir sınıf ekleyin. **Yeni Öğe Ekle** iletişim kutusu görünür.  
  
4. **Sınıf** şablonunu seçin.  
  
5. Yeni sınıfı adlandırın `UserNameInfo.vb` ve ardından **Ekle** ' ye tıklayarak yeni sınıf için kodu görüntüleyin.  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    > Anahtar sözcüğünü ve ardından yeni sınıfın adını yazarak başlangıç formunuza bir sınıf eklemek için Visual Basic **kod düzenleyicisini** kullanabilirsiniz `Class` . **Kod Düzenleyicisi** sizin için karşılık gelen bir `End Class` bildirim sağlar.  
  
6. Ve deyimleri arasına aşağıdaki kodu ekleyerek sınıf için özel bir alan tanımlayın `Class` `End Class` :  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     Alanı olarak bildirmek, `Private` yalnızca sınıfında kullanılabileceği anlamına gelir. Daha fazla erişim sağlayan gibi erişim değiştiricilerini kullanarak alanları bir sınıfın dışından kullanılabilir hale getirebilirsiniz `Public` . Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../declared-elements/access-levels.md).  
  
7. Aşağıdaki kodu ekleyerek sınıf için bir özellik tanımlayın:  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. Aşağıdaki kodu ekleyerek sınıf için bir yöntem tanımlayın:  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. Adlı bir yordam ekleyerek yeni sınıf için parametreli bir Oluşturucu tanımlayın `Sub New` :  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     `Sub New`Bu sınıfa dayalı bir nesne oluşturulduğunda Oluşturucu otomatik olarak çağrılır. Bu Oluşturucu, Kullanıcı adını tutan alanın değerini ayarlar.  
  
## <a name="to-create-a-button-to-test-the-class"></a>Sınıfı test etmek üzere bir düğme oluşturmak için
  
1. Başlangıç formunu, **Çözüm Gezgini** adına sağ tıklayıp **Görünüm Tasarımcısı**' na tıklayarak tasarım moduna değiştirin. Varsayılan olarak, Windows uygulama projeleri için başlangıç formu Form1. vb olarak adlandırılır. Ana form daha sonra görüntülenir.  
  
2. Ana forma bir düğme ekleyin ve olay işleyicisi için kodu göstermek üzere çift tıklayın `Button1_Click` . Test yordamını çağırmak için aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>Uygulamanızı çalıştırmak için
  
1. F5 tuşuna basarak uygulamanızı çalıştırın. Test yordamını çağırmak için formdaki düğmeye tıklayın. Bu, `UserName` yordamın nesne yöntemi olarak adlandırıldığından, orijinalin "Moore, BODIRE" olduğunu belirten bir ileti görüntüler `Capitalize` .  
  
2. İleti kutusunu kapatmak için **Tamam** ' ı tıklatın. `Button1 Click`Yordam, özelliğinin değerini değiştirir `UserName` ve yeni değerinin `UserName` "Worden, ali" olduğunu belirten bir ileti görüntüler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne odaklı programlama (Visual Basic)](../../concepts/object-oriented-programming.md)
- [Nesneler ve sınıflar](index.md)
