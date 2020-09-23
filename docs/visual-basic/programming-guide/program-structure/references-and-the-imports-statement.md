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
ms.openlocfilehash: 13f250e1b015e5a821da83e557033bc878a8a3b8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097910"
---
# <a name="references-and-the-imports-statement-visual-basic"></a>References ve Imports Deyimi (Visual Basic)

**Proje** menüsünde **Başvuru Ekle** komutunu seçerek dış nesneleri projeniz için kullanılabilir hale getirebilirsiniz. Visual Basic başvurular tür kitaplıkları gibi olan ancak daha fazla bilgi içeren derlemelere işaret edebilir.  
  
## <a name="the-imports-statement"></a>Imports ekstresi  

 Derlemeler bir veya daha fazla ad alanı içerir. Bir derlemeye başvuru eklediğinizde, `Imports` Bu derlemenin modül içindeki ad alanlarının görünürlüğünü denetleyen bir modüle de bir ifade ekleyebilirsiniz. `Imports`Bu ifade, benzersiz bir başvuru sağlamak için gereken ad alanının yalnızca bir kısmını kullanmanıza imkan tanıyan bir kapsam bağlamı sağlar.  
  
 `Imports`İfadesinin sözdizimi aşağıdaki gibidir:  
  
 `Imports [Aliasname =] Namespace`  
  
 `Aliasname` İçeri aktarılan bir ad alanına başvurmak için kod içinde kullanabileceğiniz kısa bir ad anlamına gelir. `Namespace` proje başvurusu aracılığıyla, proje içindeki bir tanım aracılığıyla veya önceki bir ifadeyle bulunan bir ad alanıdır `Imports` .  
  
 Modül, herhangi bir sayıda deyim içerebilir `Imports` . Varsa, varsa tüm `Option` deyimlerden sonra, diğer koddan önce gelmelidir.  
  
> [!NOTE]
> Proje başvurularını `Imports` deyimle veya `Declare` ifadesiyle karıştırmayın. Proje başvuruları, derlemelerdeki nesneler gibi dış nesneleri Visual Basic projeleri için kullanılabilir hale getirir. `Imports`İfade, proje başvurularına erişimi basitleştirmek için kullanılır, ancak bu nesnelere erişim sağlamaz. İfade, bir `Declare` dinamik bağlantı kitaplığı (dll) içinde bir dış yordama başvuru bildirmek için kullanılır.  
  
## <a name="using-aliases-with-the-imports-statement"></a>Imports Ifadesiyle diğer adları kullanma  

 `Imports`İfade, başvuruların tam adlarını açıkça yazma gereğini ortadan kaldırarak sınıfların yöntemlerine erişmeyi kolaylaştırır. Diğer adlar, bir ad alanının yalnızca bir kısmına kolay bir ad atamanızı sağlar. Örneğin, tek bir metin parçasının birden çok satırda görüntülenmesine neden olan satır başı/satır besleme sırası, <xref:Microsoft.VisualBasic.ControlChars> ad alanındaki modülün bir parçasıdır <xref:Microsoft.VisualBasic?displayProperty=nameWithType> . Diğer adı olmayan bir programda bu sabiti kullanmak için aşağıdaki kodu yazmanız gerekir:  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 `Imports` deyimler her zaman `Option` bir modüldeki deyimlerden hemen sonra gelen ilk satır olmalıdır. Aşağıdaki kod parçası, modüle bir diğer adın nasıl içeri aktarılacağını ve atanacağını gösterir <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> :  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 Bu ad alanına gelecekteki başvurular önemli ölçüde daha kısa olabilir:  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 Bir `Imports` ifade bir diğer ad içermiyorsa, içeri aktarılan ad alanı içinde tanımlanan öğeler, bir nitelik olmadan modülde kullanılabilir. Diğer ad belirtilmişse, bu ad alanı içinde yer alan adlara yönelik bir niteleyici olarak kullanılması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [Visual Basic'de Ad Alanları](namespaces.md)
- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
