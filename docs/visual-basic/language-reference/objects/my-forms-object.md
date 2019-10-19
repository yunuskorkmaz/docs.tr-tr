---
title: My. Forms nesnesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 9a0b3b9202972122aea4a7147d8d872486418264
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581863"
---
# <a name="myforms-object"></a>My.Forms Nesnesi

Geçerli projede belirtilen her bir Windows formunun örneğine erişim için özellikler sağlar.

## <a name="remarks"></a>Açıklamalar

@No__t_0 nesnesi, geçerli projede her formun bir örneğini sağlar. Özelliğin adı, özelliğin eriştiği form adıyla aynıdır.

@No__t_0 nesnesi tarafından sunulan formlara, nitelik olmadan formun adını kullanarak erişebilirsiniz. Özellik adı formun tür adıyla aynı olduğundan, bir forma varsayılan bir örnek olsa da erişmenize izin verir. Örneğin, `My.Forms.Form1.Show` `Form1.Show` eşdeğerdir.

@No__t_0 nesnesi yalnızca geçerli projeyle ilişkili formları kullanıma sunar. Başvurulan DLL 'lerde belirtilen formlara erişim sağlamaz. Bir DLL 'nin sağladığı bir forma erişmek için, formun adı dll olarak *yazılmış şekilde tam*adını kullanmanız gerekir. *FormName*.

Tüm uygulamaların açık formlarının bir koleksiyonunu almak için <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> özelliğini kullanabilirsiniz.

Nesnesi ve özellikleri yalnızca Windows uygulamaları için kullanılabilir.

## <a name="properties"></a>Özellikler

@No__t_0 nesnesinin her özelliği, geçerli projedeki bir form örneğine erişim sağlar. Özelliğin adı, özelliğin eriştiği form adı ile aynıdır ve özellik türü formun türü ile aynıdır.

> [!NOTE]
> Ad çakışması varsa, bir forma erişmek için özellik adı, \_*FormName*adlı *RootNamespace*_*ad* alanıdır. Örneğin, bu formlardan biri olan `Form1.`If adlı iki formu göz önünde bulundurun `WindowsApplication1` kök ad alanı `Namespace1`, bu forma `My.Forms.WindowsApplication1_Namespace1_Form1` aracılığıyla erişebilirsiniz.

@No__t_0 nesnesi, başlangıçta oluşturulan uygulamanın ana formunun örneğine erişim sağlar. Tüm diğer formlar için `My.Forms` nesnesi, erişildiğinde formun yeni bir örneğini oluşturur ve depolar. Bu özelliğe daha sonra erişme girişimleri, formun bu örneğini döndürür.

Bu formun özelliğine `Nothing` atayarak formu atabilirsiniz. Özellik ayarlayıcısı, formun <xref:System.Windows.Forms.Form.Close%2A> yöntemini çağırır ve sonra depolanan değere `Nothing` atar. Özelliğe `Nothing` dışında herhangi bir değer atarsanız, ayarlayıcı bir <xref:System.ArgumentException> özel durumu oluşturur.

@No__t_0 nesnesinin bir özelliğinin, `Is` veya `IsNot` işlecini kullanarak formun bir örneğini depolayıp depoladığını test edebilirsiniz. Bu işleçleri, özelliğin değerinin `Nothing` olup olmadığını denetlemek için kullanabilirsiniz.

> [!NOTE]
> Genellikle, `Is` veya `IsNot` işleci, karşılaştırmayı gerçekleştirmek için özelliğinin değerini okumalı. Ancak, özelliği şu anda `Nothing` depoluyorsa, özelliği formun yeni bir örneğini oluşturur ve sonra bu örneği döndürür. Ancak, Visual Basic derleyici `My.Forms` nesnesinin özelliklerini farklı şekilde değerlendirir ve `Is` ya da `IsNot` işlecinin değeri değiştirmeden özelliğin durumunu denetlemesini sağlar.

## <a name="example"></a>Örnek

Bu örnek, varsayılan `SidebarMenu` formun başlığını değiştirir.

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

Bu örneğin çalışması için, projenizin `SidebarMenu` adlı bir formu olması gerekir.

Bu kod, yalnızca bir Windows uygulama projesinde çalışır.

## <a name="requirements"></a>Gereksinimler

### <a name="availability-by-project-type"></a>Proje Türüne Göre Kullanılabilirlik

|Proje türü|Kullanılabilir|
|---|---|
|Windows uygulaması|**Yes**|
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
