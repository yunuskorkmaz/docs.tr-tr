---
title: 'Nasıl yapılır: Bir Nesnenin Üyelerine Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: d44b538e8413eb1412e937375e9bca77600a29b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348662"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>Nasıl yapılır: Bir Nesnenin Üyelerine Erişme (Visual Basic)

Bir nesneye başvuran bir nesne değişkeniniz varsa, genellikle bu nesnenin, yöntemleri, özellikleri, alanları ve olayları gibi üyeleriyle çalışmak istersiniz. Örneğin, yeni bir <xref:System.Windows.Forms.Form> nesnesi oluşturduktan sonra, <xref:System.Windows.Forms.Control.Text%2A> özelliğini ayarlamak veya <xref:System.Windows.Forms.Control.Focus%2A> metodunu çağırmak isteyebilirsiniz.

## <a name="accessing-members"></a>Üyelere erişme

Bir nesnenin üyelerine, ona başvuran değişken aracılığıyla erişirsiniz.

#### <a name="to-access-members-of-an-object"></a>Bir nesnenin üyelerine erişmek için

- Nesne değişkeni adı ve üye adı arasındaki üye erişim işlecini (`.`) kullanın.

    ```vb
    currentText = newForm.Text
    ```

    Üye [paylaşılmışsa](../../../../visual-basic/language-reference/modifiers/shared.md), ona erişmek için bir değişkene ihtiyacınız yoktur.

## <a name="accessing-members-of-an-object-of-known-type"></a>Bilinen türdeki bir nesnenin üyelerine erişme

Derleme zamanında bir nesnenin türünü biliyorsanız, ona başvuran bir değişken için *erken bağlamayı* kullanabilirsiniz.

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>Derleme zamanında türünü bildiğiniz bir nesnenin üyelerine erişmek için

1. Değişkene atamak istediğiniz nesnenin türünün nesne değişkenini bildirin.

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    `Option Strict On`, yalnızca <xref:System.Windows.Forms.Form> nesneleri (veya <xref:System.Windows.Forms.Form>türetilen bir türdeki nesneleri `extraForm`' a atayabilirsiniz. <xref:System.Windows.Forms.Form>için genişleyen `CType` dönüştürmeye sahip bir sınıf veya yapı tanımladıysanız, bu sınıfı veya yapıyı da `extraForm`atayabilirsiniz.

2. Nesne değişkeni adı ve üye adı arasındaki üye erişim işlecini (`.`) kullanın.

    ```vb
    extraForm.Show()
    ```

    `Option Strict` ayarının ne olduğuna bakılmaksızın <xref:System.Windows.Forms.Form> sınıfına özgü tüm yöntemlere ve özelliklere erişebilirsiniz.

## <a name="accessing-members-of-an-object-of-unknown-type"></a>Bilinmeyen türdeki bir nesnenin üyelerine erişme

Derleme zamanında bir nesnenin türünü bilmiyor değilseniz, ona başvuran herhangi bir değişken için *geç bağlamayı* kullanmanız gerekir.

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>Derleme zamanında türünü tanımadığınız bir nesnenin üyelerine erişmek için

1. Nesne [veri türünde](../../../../visual-basic/language-reference/data-types/object-data-type.md)olacak nesne değişkenini bildirin. (Bir değişkeni `Object` olarak bildirmek, <xref:System.Object?displayProperty=nameWithType>olarak bildirme ile aynıdır.)

    ```vb
    Dim someControl As Object
    ```

    `Option Strict On`, yalnızca <xref:System.Object> sınıfında tanımlanmış üyelere erişebilirsiniz.

2. Nesne değişkeni adı ve üye adı arasındaki üye erişim işlecini (`.`) kullanın.

    ```vb
    someControl.GetType()
    ```

    Nesne değişkenine atadığınız herhangi bir nesnenin üyelerine erişebilmek için `Option Strict Off`ayarlamanız gerekir. Bunu yaptığınızda derleyici, belirli bir üyenin değişkene atadığınız nesne tarafından açığa çıkarılabileceği garantisi vermez. Nesne, erişmeye çalıştığınız bir üyeyi kullanıma sunmadığından, bir <xref:System.MemberAccessException> özel durumu oluşur.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
