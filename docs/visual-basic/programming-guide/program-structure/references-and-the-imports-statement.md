---
title: References ve Imports Deyimi
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 31b4fe001f2b8a62ac30488053c57cd186020421
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347274"
---
# <a name="references-and-the-imports-statement-visual-basic"></a>References ve Imports Deyimi (Visual Basic)
**Proje** menüsünde **Başvuru Ekle** komutunu seçerek dış nesneleri projeniz için kullanılabilir hale getirebilirsiniz. Visual Basic başvurular tür kitaplıkları gibi olan ancak daha fazla bilgi içeren derlemelere işaret edebilir.  
  
## <a name="the-imports-statement"></a>Imports ekstresi  
 Derlemeler bir veya daha fazla ad alanı içerir. Bir derlemeye başvuru eklediğinizde, bu derlemenin modül içindeki ad alanlarının görünürlüğünü denetleyen bir modüle `Imports` deyiminizi de ekleyebilirsiniz. `Imports` ifade, benzersiz bir başvuru sağlamak için gereken ad alanının yalnızca bir kısmını kullanmanıza imkan tanıyan bir kapsam bağlamı sağlar.  
  
 `Imports` deyimin sözdizimi aşağıdaki gibidir:  
  
 `Imports [Aliasname =] Namespace`  
  
 `Aliasname`, içeri aktarılan bir ad alanına başvurmak için kod içinde kullanabileceğiniz kısa bir ad anlamına gelir. `Namespace`, proje başvurusu aracılığıyla veya proje içindeki bir tanım aracılığıyla ya da önceki bir `Imports` ifadesiyle kullanılabilir bir ad alanıdır.  
  
 Modül, herhangi bir sayıda `Imports` deyimi içerebilir. Varsa, varsa, herhangi bir `Option` deyimden sonra, diğer koddan önce gelmelidir.  
  
> [!NOTE]
> Proje başvurularını `Imports` ifadesiyle veya `Declare` ifadesiyle karıştırmayın. Proje başvuruları, derlemelerdeki nesneler gibi dış nesneleri Visual Basic projeleri için kullanılabilir hale getirir. `Imports` deyimleri proje başvurularına erişimi basitleştirmek için kullanılır, ancak bu nesnelere erişim sağlamaz. `Declare` deyimleri, bir dinamik bağlantı kitaplığı (DLL) içinde bir dış yordama başvuru bildirmek için kullanılır.  
  
## <a name="using-aliases-with-the-imports-statement"></a>Imports Ifadesiyle diğer adları kullanma  
 `Imports` ifade, başvuruların tam adlarını açıkça yazma gereğini ortadan kaldırarak sınıfların yöntemlerine erişmeyi kolaylaştırır. Diğer adlar, bir ad alanının yalnızca bir kısmına kolay bir ad atamanızı sağlar. Örneğin, tek bir metin parçasının birden çok satırda görüntülenmesine neden olan satır başı/satır besleme sırası, <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanındaki <xref:Microsoft.VisualBasic.ControlChars> modülünün bir parçasıdır. Diğer adı olmayan bir programda bu sabiti kullanmak için aşağıdaki kodu yazmanız gerekir:  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 `Imports` deyimleri her zaman bir modüldeki tüm `Option` deyimlerinin hemen ardından ilk satır olmalıdır. Aşağıdaki kod parçası <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> modülüne nasıl bir diğer ad aktarılacağını ve atanacağını gösterir:  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 Bu ad alanına gelecekteki başvurular önemli ölçüde daha kısa olabilir:  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 `Imports` bir ifade bir diğer ad içermiyorsa, içeri aktarılan ad alanı içinde tanımlanan öğeler, hiçbir nitelemeden modülde kullanılabilir. Diğer ad belirtilmişse, bu ad alanı içinde yer alan adlara yönelik bir niteleyici olarak kullanılması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [Visual Basic ad alanları](namespaces.md)
- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
