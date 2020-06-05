---
title: My.Forms Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 001f6fbfae2467ea0af5e98ca041b694d1e7b8f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372446"
---
# <a name="myforms-object"></a>My.Forms Nesnesi

Geçerli projede belirtilen her bir Windows formunun örneğine erişim için özellikler sağlar.

## <a name="remarks"></a>Açıklamalar

`My.Forms`Nesnesi, geçerli projede her formun bir örneğini sağlar. Özelliğin adı, özelliğin eriştiği form adıyla aynıdır.

Nesne tarafından sunulan formlara `My.Forms` , nitelik olmadan formun adını kullanarak erişebilirsiniz. Özellik adı formun tür adıyla aynı olduğundan, bir forma varsayılan bir örnek olsa da erişmenize izin verir. Örneğin, `My.Forms.Form1.Show` öğesine eşdeğerdir `Form1.Show` .

`My.Forms`Nesne yalnızca geçerli projeyle ilişkili formları kullanıma sunar. Başvurulan DLL 'lerde belirtilen formlara erişim sağlamaz. Bir DLL 'nin sağladığı bir forma erişmek için, formun adı dll olarak *yazılmış şekilde tam*adını kullanmanız gerekir. *FormName*.

<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>Tüm uygulamanın açık formlarının bir koleksiyonunu almak için özelliğini kullanabilirsiniz.

Nesnesi ve özellikleri yalnızca Windows uygulamaları için kullanılabilir.

## <a name="properties"></a>Özellikler

Nesnesinin her özelliği, `My.Forms` geçerli projedeki bir form örneğine erişim sağlar. Özelliğin adı, özelliğin eriştiği form adı ile aynıdır ve özellik türü formun türü ile aynıdır.

> [!NOTE]
> Bir ad çakışması varsa, bir forma erişmek için özellik adı, *RootNamespace**_ ad alanı* \_ *FormName*olur. Örneğin, `Form1.` Bu formlardan biri kök ad alanında `WindowsApplication1` ve ad alanında olduğunda, bu `Namespace1` formdan ' a eriştiğinizde adlı iki formu göz önünde bulundurun `My.Forms.WindowsApplication1_Namespace1_Form1` .

`My.Forms`Nesnesi, başlangıçta oluşturulan uygulamanın ana formunun örneğine erişim sağlar. Diğer tüm formlarda, `My.Forms` nesne erişildiğinde formun yeni bir örneğini oluşturur ve depolar. Bu özelliğe daha sonra erişme girişimleri, formun bu örneğini döndürür.

Form için özelliğine atayarak formu atabilirsiniz `Nothing` . Özellik ayarlayıcısı <xref:System.Windows.Forms.Form.Close%2A> formun yöntemini çağırır ve ardından `Nothing` depolanan değere atar. Özelliği dışında bir değer atarsanız `Nothing` , ayarlayıcı bir <xref:System.ArgumentException> özel durum oluşturur.

Bir `My.Forms` nesnenin özelliğinin, veya işlecini kullanarak formun bir örneğini depolayıp depomadığını test edebilirsiniz `Is` `IsNot` . Özelliğin değerinin olup olmadığını denetlemek için bu işleçleri kullanabilirsiniz `Nothing` .

> [!NOTE]
> Genellikle, `Is` veya `IsNot` işlecinin karşılaştırmayı gerçekleştirmek için özelliğinin değerini okuması gerekir. Ancak, özelliği şu anda depoluyorsa `Nothing` , özelliği formun yeni bir örneğini oluşturur ve sonra bu örneği döndürür. Ancak, Visual Basic Derleyicisi `My.Forms` nesnenin özelliklerini farklı şekilde değerlendirir ve `Is` veya `IsNot` işlecinin değeri değiştirmeden özelliğin durumunu denetlemesini sağlar.

## <a name="example"></a>Örnek

Bu örnek, varsayılan formun başlığını değiştirir `SidebarMenu` .

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

Bu örneğin çalışması için projenizin adında bir form olması gerekir `SidebarMenu` .

Bu kod, yalnızca bir Windows uygulama projesinde çalışır.

## <a name="requirements"></a>Gereksinimler

### <a name="availability-by-project-type"></a>Proje Türüne Göre Kullanılabilirlik

|Proje türü|Kullanılabilir|
|---|---|
|Windows uygulaması|**Evet**|
|Sınıf Kitaplığı|No|
|Konsol Uygulaması|No|
|Windows Denetim Kitaplığı|No|
|Web Denetim Kitaplığı|No|
|Windows Hizmeti|No|
|Web Sitesi|No|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [Nesneler](index.md)
- [Is İşleci](../operators/is-operator.md)
- [IsNot İşleci](../operators/isnot-operator.md)
- [Uygulama Formlarına Erişme](../../developing-apps/programming/accessing-application-forms.md)
