---
title: My.Forms Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: db86704fdc8120ccac5f4489c80a515834ad888f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350368"
---
# <a name="myforms-object"></a>My.Forms Nesnesi

Geçerli projede belirtilen her bir Windows formunun örneğine erişim için özellikler sağlar.

## <a name="remarks"></a>Açıklamalar

`My.Forms` nesnesi, geçerli projede her formun bir örneğini sağlar. Özelliğin adı, özelliğin eriştiği form adıyla aynıdır.

`My.Forms` nesnesi tarafından sunulan formlara, nitelik olmadan formun adını kullanarak erişebilirsiniz. Özellik adı formun tür adıyla aynı olduğundan, bir forma varsayılan bir örnek olsa da erişmenize izin verir. Örneğin, `My.Forms.Form1.Show` `Form1.Show`eşdeğerdir.

`My.Forms` nesnesi yalnızca geçerli projeyle ilişkili formları kullanıma sunar. Başvurulan DLL 'lerde belirtilen formlara erişim sağlamaz. Bir DLL 'nin sağladığı bir forma erişmek için, formun adı dll olarak *yazılmış şekilde tam*adını kullanmanız gerekir. *FormName*.

Tüm uygulamaların açık formlarının bir koleksiyonunu almak için <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> özelliğini kullanabilirsiniz.

Nesnesi ve özellikleri yalnızca Windows uygulamaları için kullanılabilir.

## <a name="properties"></a>Özellikler

`My.Forms` nesnesinin her özelliği, geçerli projedeki bir form örneğine erişim sağlar. Özelliğin adı, özelliğin eriştiği form adı ile aynıdır ve özellik türü formun türü ile aynıdır.

> [!NOTE]
> Ad çakışması varsa, bir forma erişmek için özellik adı,\_*FormName*adlı *RootNamespace*_*ad* alanıdır. Örneğin, bu formlardan biri kök ad alanında `WindowsApplication1` ve ad alanı `Namespace1``Form1.`adlı iki formu göz önünde bulundurun. Bu forma `My.Forms.WindowsApplication1_Namespace1_Form1`aracılığıyla erişebilirsiniz.

`My.Forms` nesnesi, başlangıçta oluşturulan uygulamanın ana formunun örneğine erişim sağlar. Tüm diğer formlar için `My.Forms` nesnesi, erişildiğinde formun yeni bir örneğini oluşturur ve depolar. Bu özelliğe daha sonra erişme girişimleri, formun bu örneğini döndürür.

Bu formun özelliğine `Nothing` atayarak formu atabilirsiniz. Özellik ayarlayıcısı, formun <xref:System.Windows.Forms.Form.Close%2A> yöntemini çağırır ve sonra depolanan değere `Nothing` atar. Özelliğe `Nothing` dışında herhangi bir değer atarsanız, ayarlayıcı bir <xref:System.ArgumentException> özel durumu oluşturur.

`My.Forms` nesnesinin bir özelliğinin, `Is` veya `IsNot` işlecini kullanarak formun bir örneğini depolayıp depoladığını test edebilirsiniz. Bu işleçleri, özelliğin değerinin `Nothing`olup olmadığını denetlemek için kullanabilirsiniz.

> [!NOTE]
> Genellikle, `Is` veya `IsNot` işleci, karşılaştırmayı gerçekleştirmek için özelliğinin değerini okumalı. Ancak, özelliği şu anda `Nothing`depoluyorsa, özelliği formun yeni bir örneğini oluşturur ve sonra bu örneği döndürür. Ancak, Visual Basic derleyici `My.Forms` nesnesinin özelliklerini farklı şekilde değerlendirir ve `Is` ya da `IsNot` işlecinin değeri değiştirmeden özelliğin durumunu denetlemesini sağlar.

## <a name="example"></a>Örnek

Bu örnek, varsayılan `SidebarMenu` formun başlığını değiştirir.

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

Bu örneğin çalışması için, projenizin `SidebarMenu`adlı bir formu olması gerekir.

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
