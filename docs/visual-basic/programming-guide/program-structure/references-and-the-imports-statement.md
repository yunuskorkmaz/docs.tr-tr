---
title: References ve Imports Deyimi (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 60c62eae57ae127fcbb860fe72853604802cccd9
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="references-and-the-imports-statement-visual-basic"></a>References ve Imports Deyimi (Visual Basic)
Dış nesneleri kullanılabilir projenize seçerek yapabileceğiniz **Başvuru Ekle** komutunu **proje** menüsü. Başvurur [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tür kitaplıklarının ancak daha fazla bilgi içeriyor gibi olan derlemeler için işaret edebilir.  
  
## <a name="the-imports-statement"></a>Imports deyimi  
 Derlemeler, bir veya daha fazla ad içerir. Bir derleme başvurusu eklediğinizde, bu da ekleyebilirsiniz bir `Imports` o derlemenin ad alanları modülü içinde görünürlüğünü denetleyen bir modüle deyimi. `Imports` Deyimi yalnızca benzersiz bir başvuruyu sağlamak gerekli ad alanı bölümünü kullanmanıza olanak sağlayan bir kapsam bağlamı sağlar.  
  
 `Imports` Deyiminin aşağıdaki söz dizimini şunlardır:  
  
 `Imports` [`|``Aliasname` =] `Namespace`  
  
 `Aliasname`kod içinde içeri aktarılan ad alanına başvurmak için kullanabileceğiniz kısa bir ad belirtir. `Namespace`proje başvurusu tanımı projesi içinde veya önceki bir ad alanı aracılığıyla kullanılabilir olan `Imports` deyimi.  
  
 Bir modül herhangi bir sayıda içerebilir `Imports` deyimleri. Herhangi bir sonra görünmelidir `Option` deyimleri, varsa, ancak başka bir kod önce.  
  
> [!NOTE]
>  Proje başvuruları ile karıştırmayın `Imports` deyimi veya `Declare` deyimi. Proje başvuruları derlemeler, nesneleri gibi dış nesneler için kullanılabilir duruma [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projeleri. `Imports` Deyimi proje başvuruları erişimi kolaylaştırmak için kullanılır, ancak bu nesnelere erişimi sağlamaz. `Declare` Deyimi, bir dinamik bağlantı kitaplığı (DLL) dış bir yordamda başvuru bildirmek için kullanılır.  
  
## <a name="using-aliases-with-the-imports-statement"></a>Imports deyimi ile diğer adlarını kullanma  
 `Imports` Deyimi kolaylaştırır erişim yöntemlerine sınıfların açıkça tam olarak nitelenmiş adlar başvuruları yazma gereğini ortadan kaldırarak. Diğer adlar, bir ad alanının yalnızca bir parçası yaşamanızı bir ad atamak olanak tanır. Örneğin, satır başı/tek bir birden çok satırda görüntülenecek metni neden dizisi satır besleme parçası olan <xref:Microsoft.VisualBasic.ControlChars> modülünde <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanı. Bu sabit bir diğer ad olmadan bir programda kullanmak için aşağıdaki kod yazmanız gerekir:  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 `Imports`deyimleri her zaman hemen herhangi aşağıdaki ilk satırı olmalıdır `Option` bir modül deyimlerinde. Aşağıdaki kod parçası, almak ve bir diğer ad atamak gösterilmiştir <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> Modülü:  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 Bu ad alanına gelecek başvuruları önemli ölçüde daha kısa olabilir:  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 Varsa bir `Imports` deyimi bir diğer ad içermez, içeri aktarılan ad alanında tanımlanan öğe niteliğe olmadan modül kullanılabilir. Diğer ad belirtilmezse, bir niteleyici olarak ad alanında yer alan adları için kullanılmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.ControlChars>  
 <xref:Microsoft.VisualBasic>  
   
 [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Derlemeler ve Genel Derleme Önbelleği](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Nasıl yapılır: Komut Satırını Kullanarak Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
