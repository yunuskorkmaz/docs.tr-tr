---
title: References ve Imports Deyimi (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 89d360e5caa3cdb0dd1ecb985ea7ba727e5a6d9d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208523"
---
# <a name="references-and-the-imports-statement-visual-basic"></a>References ve Imports Deyimi (Visual Basic)
Dış nesneler kullanılabilir projenize seçerek yapabileceğiniz **Başvuru Ekle** komutunu **proje** menüsü. Başvuruları Visual Basic'te tür kitaplıkları, ancak daha fazla bilgi içeren gibi olan derlemeler için işaret edebilir.  
  
## <a name="the-imports-statement"></a>Imports deyimi  
 Derlemeler, bir veya daha fazla ad alanı içerir. Bir derlemeye bir başvuru eklediğinizde, bu da ekleyebilirsiniz bir `Imports` o derlemenin ad alanları modülü içinde görünürlüğünü denetleyen bir modüle deyimi. `Imports` Deyimi yalnızca bir benzersiz başvuru sağlamanız için gereken ad alanının bölümü kullanmanıza olanak sağlayan bir kapsam bağlamı sağlar.  
  
 `Imports` Deyimi sözdizimine sahiptir:  
  
 `Imports` [`|``Aliasname` =] `Namespace`  
  
 `Aliasname` kod içinde bir içeri aktarılan ad alanına başvurmak için kullanabileceğiniz bir kısa ad belirtir. `Namespace` Proje içinde bir tanımı veya önceki bir proje başvurusu bir ad alanı aracılığıyla kullanılabilir olan `Imports` deyimi.  
  
 Bir modülün herhangi bir sayıda içerebilir `Imports` deyimleri. Herhangi bir sonra görünmelidir `Option` deyimleri, varsa, ancak herhangi bir kod önce.  
  
> [!NOTE]
>  Proje başvuruları ile karıştırmayın `Imports` deyimi veya `Declare` deyimi. Proje başvuruları, derlemelere nesneleri gibi dış nesneleri Visual Basic projeleri kullanılabilmesini sağlar. `Imports` Deyimi proje başvuruları erişimini basitleştirmek için kullanılır, ancak bu nesnelere erişimi sağlamaz. `Declare` Deyimi bir dış yordam bir dinamik bağlantı kitaplığı (DLL) içinde bir başvuru bildirmek için kullanılır.  
  
## <a name="using-aliases-with-the-imports-statement"></a>Imports deyimi ile diğer adların kullanımı  
 `Imports` Deyimi kolaylaştırır, sınıfların erişim yöntemlerine açıkça tam olarak nitelenmiş adlar başvuru türüne gereksinimini ortadan kaldırarak. Diğer adlar, daha kolay adı bir ad alanının yalnızca bir bölümü atamak sağlar. Örneğin, satır başı/birden çok satırda görüntülenecek metni tek bir parçasını neden dizisi satır besleme parçası olan <xref:Microsoft.VisualBasic.ControlChars> modülünde <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanı. Bu sabit bir diğer ad olmadan bir programda kullanmak için aşağıdaki kod yazmanız gerekir:  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 `Imports` deyimleri her zaman takip herhangi ilk satırı olmalıdır `Option` Modül içindeki deyimler. Aşağıdaki kod parçası, içeri aktarma ve diğer ad atamak gösterilmektedir <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> Modülü:  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 Bu ad gelecekte başvurular önemli ölçüde daha kısa olabilir:  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 Varsa bir `Imports` deyimi bir diğer ad içermez, içeri aktarılan ad alanı içinde tanımlanan öğeler, nitelik olmadan bir modülde kullanılabilir. Diğer ad belirtilmezse, bu Niteleyici olarak bu ad alanı içinde yer alan adları için kullanılmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
- [Derlemeler ve Genel Derleme Önbelleği](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
- [Nasıl yapılır: Komut Satırını Kullanarak Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)  
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
