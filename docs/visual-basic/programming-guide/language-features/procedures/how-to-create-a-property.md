---
title: 'Nasıl yapılır: Özellik Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: ee5a9f687765ce064eb3c3f84218ed36eb916d9d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349711"
---
# <a name="how-to-create-a-property-visual-basic"></a>Nasıl yapılır: Özellik Oluşturma (Visual Basic)
Bir `Property` ifadesiyle bir `End Property` ifadesiyle özellik tanımını çevreedersiniz. Bu tanımda bir `Get` yordamı, `Set` yordamı veya her ikisini de tanımlarsınız. Tüm özellik kodu bu yordamların içinde yer alır.  
  
 `Get` yordam özelliğin değerini alır ve `Set` yordamı bir değeri depolar. Özelliğin okuma/yazma erişimine sahip olmasını istiyorsanız her iki yordamı da tanımlamanız gerekir. Salt okunurdur bir özellik için yalnızca `Get`tanımlar ve salt yazılır bir özellik için yalnızca `Set`tanımlarsınız.  
  
### <a name="to-create-a-property"></a>Bir özellik oluşturmak için  
  
1. Herhangi bir özellik veya yordamın dışında, bir [Property ifadesini](../../../../visual-basic/language-reference/statements/property-statement.md)ve ardından bir `End Property` ifadesini kullanın.  
  
2. Özelliği parametreleri alırsa, yordamın adı ile `Property` anahtar sözcüğünü, sonra parantez içindeki parametre listesini izleyin.  
  
3. Özelliğin değerinin veri türünü belirtmek için bir `As` yan tümcesiyle ayraçları izleyin. Salt yazılır bir özellik için bile veri türünü belirtmeniz gerekir.  
  
4. `Get` ve `Set` yordamlarını uygun şekilde ekleyin. Aşağıdaki yönergelere bakın.  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>Bir özellik değeri alan bir Get yordamı oluşturmak için  
  
1. `Property` ve `End Property` deyimleri arasında, bir [Get deyimi](../../../../visual-basic/language-reference/statements/get-statement.md)ve ardından bir `End Get` deyimi yazın. `Get` yordamı için herhangi bir parametre tanımlamanız gerekmez.  
  
2. `Get` ve `End Get` deyimleri arasında özelliğin değerini almak için kod deyimlerini yerleştirin. Bu kod, özelliğin değerini oluşturma ve döndürmenin yanı sıra diğer hesaplamalar ve veri düzenlemeleri içerebilir.  
  
3. Özelliğin değerini çağıran koda döndürmek için bir `Return` ifadesini kullanın.  
  
 Okuma-yazma özelliği ve salt okunurdur özelliği için bir `Get` yordamı yazmalısınız. Salt yazılır bir özellik için `Get` yordamı tanımlamamalısınız.  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>Özelliğin değerini yazan bir ayarlama yordamı oluşturmak için  
  
1. `Property` ve `End Property` deyimleri arasında bir [set deyimi](../../../../visual-basic/language-reference/statements/set-statement.md)ve ardından bir `End Set` deyimi yazın.  
  
2. `Set` bildiriminde, parantez içinde bir parametre listesi ile `Set` anahtar sözcüğünü izleyin. Bu parametre listesi, çağıran kodun geçirilmiş değeri için en az bir değer parametresi içermelidir. Bu değer parametresinin varsayılan adı `Value`, ancak uygunsa, farklı bir ad kullanabilirsiniz. Değer parametresi, özelliğin kendisiyle aynı veri türüne sahip olmalıdır.  
  
3. `Set` ve `End Set` deyimleri arasındaki özellikte bir değeri depolamak için kod deyimlerini yerleştirin. Bu kod, özelliğin değerini doğrulamaya ve depolamaya ek olarak diğer hesaplamalar ve veri düzenlemeleri içerebilir.  
  
4. Çağıran kodun sağladığı değeri kabul etmek için value parametresini kullanın. Bu değeri doğrudan bir atama deyiminde saklayabilir veya depolanacağı iç değeri hesaplamak için bir ifadede kullanabilirsiniz.  
  
 Okuma-yazma özelliği için ve salt yazılır bir özellik için `Set` yordamı yazmalısınız. Salt okunurdur özelliği için `Set` yordam tanımlamanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tam adı iki anayent adı, ilk adı ve soyadı olarak depolayan bir okuma/yazma özelliği oluşturur. Çağıran kod `fullName`okurken, `Get` yordamı iki anayent adını birleştirir ve tam adı döndürür. Çağıran kod yeni bir tam ad atarken, `Set` yordamı onu iki anayada bölmek için çalışır. Bir boşluk bulamazsa, ilk ad olarak tümünü depolar.  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 Aşağıdaki örnek, `fullName`Özellik yordamlarına yapılan tipik çağrıları gösterir. İlk çağrı, özellik değerini ayarlar ve ikinci çağrı onu alır.  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Visual Basic Özellikler ve değişkenler arasındaki farklar](./differences-between-properties-and-variables.md)
- [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Nasıl yapılır: Bir Özellik Yordamı Çağırma](./how-to-call-a-property-procedure.md)
- [Nasıl yapılır: Visual Basic varsayılan bir özellik bildirme ve çağırma](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir Özelliğe Değer Ekleme](./how-to-put-a-value-in-a-property.md)
- [Nasıl yapılır: Bir Özellikten Değer Alma](./how-to-get-a-value-from-a-property.md)
