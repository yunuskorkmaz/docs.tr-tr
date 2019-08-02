---
title: 'Nasıl yapılır: Bir nesnenin üyelerine erişim (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 882046b829ade2da7c10b3db4c0d6c9ca9f3d579
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630836"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>Nasıl yapılır: Bir nesnenin üyelerine erişim (Visual Basic)

Bir nesneye başvuran bir nesne değişkeniniz varsa, genellikle bu nesnenin, yöntemleri, özellikleri, alanları ve olayları gibi üyeleriyle çalışmak istersiniz. Örneğin, yeni <xref:System.Windows.Forms.Form> bir nesne oluşturduktan sonra, <xref:System.Windows.Forms.Control.Text%2A> özelliğini ayarlamak veya <xref:System.Windows.Forms.Control.Focus%2A> metodunu çağırmak isteyebilirsiniz.

## <a name="accessing-members"></a>Üyelere erişme

Bir nesnenin üyelerine, ona başvuran değişken aracılığıyla erişirsiniz.

#### <a name="to-access-members-of-an-object"></a>Bir nesnenin üyelerine erişmek için

- Nesne değişkeni adı ve üye adı arasındaki`.`üye erişim işlecini () kullanın.

    ```vb
    currentText = newForm.Text
    ```

    Üye paylaşılmışsa, [](../../../../visual-basic/language-reference/modifiers/shared.md)ona erişmek için bir değişkene ihtiyacınız yoktur.

## <a name="accessing-members-of-an-object-of-known-type"></a>Bilinen türdeki bir nesnenin üyelerine erişme

Derleme zamanında bir nesnenin türünü biliyorsanız, ona başvuran bir değişken için *erken bağlamayı* kullanabilirsiniz.

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>Derleme zamanında türünü bildiğiniz bir nesnenin üyelerine erişmek için

1. Değişkene atamak istediğiniz nesnenin türünün nesne değişkenini bildirin.

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    İle `Option Strict On`, yalnızca <xref:System.Windows.Forms.Form> nesneleri (veya öğesinden <xref:System.Windows.Forms.Form>türetilmiş bir `extraForm`türün nesnelerini) atayabilirsiniz. Üzerinde genişleyen `CType` `extraForm`dönüştürmeye sahip bir sınıf veya yapı tanımladıysanız ,busınıfaveyayapıyadeatayabilirsiniz.<xref:System.Windows.Forms.Form>

2. Nesne değişkeni adı ve üye adı arasındaki`.`üye erişim işlecini () kullanın.

    ```vb
    extraForm.Show()
    ```

    Ayarın ne olduğuna bakılmaksızın <xref:System.Windows.Forms.Form> sınıfa özgü tüm yöntemlere ve özelliklere erişebilirsiniz. `Option Strict`

## <a name="accessing-members-of-an-object-of-unknown-type"></a>Bilinmeyen türdeki bir nesnenin üyelerine erişme

Derleme zamanında bir nesnenin türünü bilmiyor değilseniz, ona başvuran herhangi bir değişken için *geç bağlamayı* kullanmanız gerekir.

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>Derleme zamanında türünü tanımadığınız bir nesnenin üyelerine erişmek için

1. Nesne [veri türünde](../../../../visual-basic/language-reference/data-types/object-data-type.md)olacak nesne değişkenini bildirin. (Bir değişkeni `Object` olarak bildirmek ile aynı <xref:System.Object?displayProperty=nameWithType>şekilde bildirme.)

    ```vb
    Dim someControl As Object
    ```

    İle `Option Strict On`, yalnızca <xref:System.Object> sınıfında tanımlanmış üyelere erişebilirsiniz.

2. Nesne değişkeni adı ve üye adı arasındaki`.`üye erişim işlecini () kullanın.

    ```vb
    someControl.GetType()
    ```

    Nesne değişkenine atadığınız herhangi bir nesnenin üyelerine erişebilmek için, öğesini ayarlamanız `Option Strict Off`gerekir. Bunu yaptığınızda derleyici, belirli bir üyenin değişkene atadığınız nesne tarafından açığa çıkarılabileceği garantisi vermez. Nesne, erişmeye çalıştığınız bir üyeyi kullanıma sunmadığından, bir <xref:System.MemberAccessException> özel durum oluşur.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
