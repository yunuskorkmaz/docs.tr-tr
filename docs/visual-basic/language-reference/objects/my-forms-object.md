---
title: My. Forms nesnesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 9fa5c77dd12c98100e3d17fc473a6802180d1e32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965978"
---
# <a name="myforms-object"></a>My.Forms Nesnesi
Geçerli projede belirtilen her bir Windows formunun örneğine erişim için özellikler sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 Nesnesi `My.Forms` , geçerli projede her formun bir örneğini sağlar. Özelliğin adı, özelliğin eriştiği form adıyla aynıdır.   
  
 `My.Forms` Nesne tarafından sunulan formlara, nitelik olmadan formun adını kullanarak erişebilirsiniz. Özellik adı formun tür adıyla aynı olduğundan, bir forma varsayılan bir örnek olsa da erişmenize izin verir. Örneğin, `My.Forms.Form1.Show` öğesine `Form1.Show`eşdeğerdir.  
  
 `My.Forms` Nesne yalnızca geçerli projeyle ilişkili formları kullanıma sunar. Başvurulan DLL 'lerde belirtilen formlara erişim sağlamaz. Bir DLL 'nin sağladığı bir forma erişmek için, formun adı dll olarak yazılmış şekilde tam adını kullanmanız gerekir. *FormName*.  
  
 Tüm uygulamanın açık formlarının <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> bir koleksiyonunu almak için özelliğini kullanabilirsiniz.  
  
 Nesnesi ve özellikleri yalnızca Windows uygulamaları için kullanılabilir.  
  
## <a name="properties"></a>Özellikler  
 `My.Forms` Nesnesinin her özelliği, geçerli projedeki bir form örneğine erişim sağlar. Özelliğin adı, özelliğin eriştiği form adı ile aynıdır ve özellik türü formun türü ile aynıdır.  
  
> [!NOTE]
> Bir ad çakışması varsa, bir forma erişmek için özellik adı,\_ *RootNamespace*_ ad alanı*FormName*olur. Örneğin, bu formlardan biri kök ad `Form1.` `WindowsApplication1` alanında ve ad `Namespace1`alanında olduğunda, bu formdan `My.Forms.WindowsApplication1_Namespace1_Form1`' a eriştiğinizde adlı iki formu göz önünde bulundurun.  
  
 `My.Forms` Nesnesi, başlangıçta oluşturulan uygulamanın ana formunun örneğine erişim sağlar. Diğer tüm formlarda, `My.Forms` nesne erişildiğinde formun yeni bir örneğini oluşturur ve depolar. Bu özelliğe daha sonra erişme girişimleri, formun bu örneğini döndürür.  
  
 Form için özelliğine atayarak `Nothing` formu atabilirsiniz. Özellik ayarlayıcısı formun <xref:System.Windows.Forms.Form.Close%2A> yöntemini çağırır ve ardından depolanan değere atar `Nothing` . Özelliği dışında bir değer `Nothing` atarsanız, ayarlayıcı bir <xref:System.ArgumentException> özel durum oluşturur.  
  
 Bir `My.Forms` nesnenin özelliğinin, `Is` veya `IsNot` işlecini kullanarak formun bir örneğini depolayıp depomadığını test edebilirsiniz. Özelliğin değerinin olup olmadığını denetlemek için bu işleçleri kullanabilirsiniz `Nothing`.  
  
> [!NOTE]
> Genellikle, `Is` veya `IsNot` işlecinin karşılaştırmayı gerçekleştirmek için özelliğinin değerini okuması gerekir. Ancak, özelliği şu anda depoluyorsa `Nothing`, özelliği formun yeni bir örneğini oluşturur ve sonra bu örneği döndürür. Ancak, Visual Basic Derleyicisi `My.Forms` nesnenin özelliklerini farklı şekilde değerlendirir ve `Is` veya `IsNot` işlecinin değeri değiştirmeden özelliğin durumunu denetlemesini sağlar.  
  
## <a name="example"></a>Örnek  
 Bu örnek, varsayılan `SidebarMenu` formun başlığını değiştirir.  
  
 [!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]  
  
 Bu örneğin çalışması için projenizin adında `SidebarMenu`bir form olması gerekir.  
  
 Bu kod, yalnızca bir Windows uygulama projesinde çalışır.  
  
## <a name="requirements"></a>Gereksinimler  
  
### <a name="availability-by-project-type"></a>Proje Türüne Göre Kullanılabilirlik  
  
|Proje türü|Kullanılabilir|  
|---|---|  
|Windows uygulaması|**Evet**|  
|Sınıf Kitaplığı|Hayır|  
|Konsol Uygulaması|Hayır|  
|Windows Denetim Kitaplığı|Hayır|  
|Web Denetim Kitaplığı|Hayır|  
|Windows Hizmeti|Hayır|  
|Web Sitesi|Hayır|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [Nesneler](../../../visual-basic/language-reference/objects/index.md)
- [Is İşleci](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot İşleci](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Uygulama Formlarına Erişme](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
