---
title: "Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7824742459fca355c0043ad8ed20a26330402c05
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a><span data-ttu-id="f58ce-102">Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f58ce-102">How to: Determine Whether Two Objects Are Related (Visual Basic)</span></span>
<span data-ttu-id="f58ce-103">Varsa, oluşturuldukları sınıflar arasındaki ilişkiyi belirlemek için iki nesne karşılaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f58ce-103">You can compare two objects to determine the relationship, if any, between the classes from which they are created.</span></span> <span data-ttu-id="f58ce-104"><xref:System.Type.IsInstanceOfType%2A> Yöntemi <xref:System.Type?displayProperty=nameWithType> sınıf döndürür `True` belirtilen sınıf geçerli sınıfından devralan veya geçerli türü belirtilen sınıfı tarafından desteklenen bir arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="f58ce-104">The <xref:System.Type.IsInstanceOfType%2A> method of the <xref:System.Type?displayProperty=nameWithType> class returns `True` if the specified class inherits from the current class, or if the current type is an interface supported by the specified class.</span></span>  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a><span data-ttu-id="f58ce-105">Bir nesne başka bir nesnenin sınıf veya arabirim devralır belirlemek için</span><span class="sxs-lookup"><span data-stu-id="f58ce-105">To determine if one object inherits from another object's class or interface</span></span>  
  
1.  <span data-ttu-id="f58ce-106">Düşündüğünüz bir nesne üzerinde taban türü olamaz, çağırma <xref:System.Object.GetType%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f58ce-106">On the object you think might be of the base type, invoke the <xref:System.Object.GetType%2A> method.</span></span>  
  
2.  <span data-ttu-id="f58ce-107">Üzerinde <xref:System.Type?displayProperty=nameWithType> tarafından döndürülen nesne <xref:System.Object.GetType%2A>, çağırma <xref:System.Type.IsInstanceOfType%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f58ce-107">On the <xref:System.Type?displayProperty=nameWithType> object returned by <xref:System.Object.GetType%2A>, invoke the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>  
  
3.  <span data-ttu-id="f58ce-108">İçin bağımsız değişken listesinde <xref:System.Type.IsInstanceOfType%2A>, düşündüğünüz nesnesi, türetilen tür olabilir belirtin.</span><span class="sxs-lookup"><span data-stu-id="f58ce-108">In the argument list for <xref:System.Type.IsInstanceOfType%2A>, specify the object you think might be of the derived type.</span></span>  
  
     <span data-ttu-id="f58ce-109"><xref:System.Type.IsInstanceOfType%2A>döndürür `True` kendi bağımsız değişken türü devraldığı varsa <xref:System.Type?displayProperty=nameWithType> nesne türü.</span><span class="sxs-lookup"><span data-stu-id="f58ce-109"><xref:System.Type.IsInstanceOfType%2A> returns `True` if its argument type inherits from the <xref:System.Type?displayProperty=nameWithType> object type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f58ce-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="f58ce-110">Example</span></span>  
 <span data-ttu-id="f58ce-111">Aşağıdaki örnek, bir nesne başka bir nesnenin sınıfından türetilen bir sınıfı temsil edip etmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="f58ce-111">The following example determines whether one object represents a class derived from another object's class.</span></span>  
  
```  
Public Class baseClass  
End Class  
Public Class derivedClass : Inherits baseClass  
End Class  
Public Class testTheseClasses  
    Public Sub seeIfRelated()  
        Dim baseObj As Object = New baseClass()  
        Dim derivedObj As Object = New derivedClass()  
        Dim related As Boolean  
        related = baseObj.GetType().IsInstanceOfType(derivedObj)  
        MsgBox(CStr(related))  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="f58ce-112">İki nesne değişkenleri çağrısında beklenmeyen yerleşimini Not <xref:System.Type.IsInstanceOfType%2A>.</span><span class="sxs-lookup"><span data-stu-id="f58ce-112">Note the unexpected placement of the two object variables in the call to <xref:System.Type.IsInstanceOfType%2A>.</span></span> <span data-ttu-id="f58ce-113">Beklenen temel türü oluşturmak için kullanılan <xref:System.Type?displayProperty=nameWithType> sınıfı ve beklenen türetilen tür bağımsız değişkeni olarak geçirilir <xref:System.Type.IsInstanceOfType%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f58ce-113">The supposed base type is used to generate the <xref:System.Type?displayProperty=nameWithType> class, and the supposed derived type is passed as an argument to the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f58ce-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f58ce-114">See Also</span></span>  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.IsInstanceOfType%2A>  
 [<span data-ttu-id="f58ce-115">Nesne veri türü</span><span class="sxs-lookup"><span data-stu-id="f58ce-115">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="f58ce-116">Nesne değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f58ce-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="f58ce-117">Nesne değişkeni değerleri</span><span class="sxs-lookup"><span data-stu-id="f58ce-117">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="f58ce-118">Nasıl yapılır: iki nesnenin aynı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="f58ce-118">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
