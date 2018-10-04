---
title: My.Forms nesnesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: d15765b7673f321d4362ceea0adb73959a7e7726
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582664"
---
# <a name="myforms-object"></a>My.Forms Nesnesi
Geçerli projede bildirilen her Windows formunu örneğini erişmek için özellikleri sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 `My.Forms` Nesne örneği geçerli projedeki her bir form sağlar. Özelliğin adı özelliği erişen adı ile aynıdır.   
  
 Tarafından sağlanan forms erişebileceğiniz `My.Forms` nitelik olmadan formun adını kullanarak nesne. Özellik adı, formun tür adıyla aynı olduğundan, bu varsayılan bir örnek varmış gibi bir form erişmenize olanak sağlar. Örneğin, `My.Forms.Form1.Show` eşdeğerdir `Form1.Show`.  
  
 `My.Forms` Nesnesi yalnızca geçerli projeyle ilişkili formları kullanıma sunar. DLL içinde bildirilen formlara erişimi sağlamaz. Bir DLL sağlayan bir forma erişmek için tam olarak yazılan formun adını kullanın *dll*. *Formadı*.  
  
 Kullanabileceğiniz <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> uygulamanın tüm açık form koleksiyonu alınacağı özellik.  
  
 Nesne ve özellikleri, yalnızca Windows uygulamaları için kullanılabilir.  
  
## <a name="properties"></a>Özellikler  
 Her bir özelliği `My.Forms` nesnesi geçerli proje içinde bir formun örneğine erişim sağlar. Özelliğin adı özelliği erişen adı ile aynıdır ve özellik türü form denetiminin türü ile aynıdır.  
  
> [!NOTE]
>  Bir ad çakışması varsa, bir forma erişmek için özellik adı olan *RootNamespace*_*Namespace*\_*formadı*. Örneğin, iki forms adlı göz önünde bulundurun `Form1.`biçimlerinden kök ad alanında olup olmadığını `WindowsApplication1` ve ad alanındaki `Namespace1`, bu formu üzerinden eriştiğiniz `My.Forms.WindowsApplication1_Namespace1_Form1`.  
  
 `My.Forms` Nesnesi başlangıç sırasında oluşturulan uygulamanın ana formu örneğine erişim sağlar. Diğer tüm biçimler için `My.Forms` nesnesi erişilir ve depolar, formun yeni bir örneğini oluşturur. Bu özelliğe erişmek için sonraki denemeler form örneğini döndürür.  
  
 Atayarak bir formu dispose `Nothing` özelliğine oluşturan. Özellik ayarlayıcı çağrılarında <xref:System.Windows.Forms.Form.Close%2A> form ve ardından atar yöntemi `Nothing` depolanmış değere. Dışında herhangi bir değer atamanız durumunda `Nothing` ayarlayıcı özelliğine atar bir <xref:System.ArgumentException> özel durum.  
  
 Bir özelliği olup olmadığını sınayabilirsiniz `My.Forms` nesneyi kullanarak bir formun örneğini depolar `Is` veya `IsNot` işleci. Bu işleçler özelliğinin değeri olup olmadığını denetlemek için kullanabileceğiniz `Nothing`.  
  
> [!NOTE]
>  Genellikle, `Is` veya `IsNot` işleci olan bir karşılaştırma yapmak için özelliğinin değeri okunamıyor. Ancak, bu özellik şu anda depoluyorsa `Nothing`, özellik formun yeni bir örneğini oluşturur ve bu örneği döndürür. Ancak, Visual Basic derleyici özelliklerini işler `My.Forms` sağlar ve farklı nesne `Is` veya `IsNot` değerini değiştirmeden özelliğinin durumu denetlemek için işleci.  
  
## <a name="example"></a>Örnek  
 Bu örnekte varsayılan başlığın değiştiğine `SidebarMenu` formu.  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 Çalışmak bu örnek için projenizde adlı bir form olmalı `SidebarMenu`.  
  
 Bu kod yalnızca bir Windows uygulaması projesi içinde çalışır.  
  
## <a name="requirements"></a>Gereksinimler  
  
### <a name="availability-by-project-type"></a>Proje Türüne Göre Kullanılabilirlik  
  
|Proje türü|Kullanılabilir|  
|---|---|  
|Windows uygulama|**Evet**|  
|Sınıf Kitaplığı|Hayır|  
|Konsol Uygulaması|Hayır|  
|Windows Denetim Kitaplığı|Hayır|  
|Web Denetim Kitaplığı|Hayır|  
|Windows Hizmeti|Hayır|  
|Web Sitesi|Hayır|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Form.Close%2A>  
 [Nesneler](../../../visual-basic/language-reference/objects/index.md)  
 [Is İşleci](../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot İşleci](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Uygulama Formlarına Erişme](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
