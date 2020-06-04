---
title: 'Nasıl yapılır: Bir Nesnenin Üyelerine Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 2826a3c98b9f19b08cc943d0f67cdd34ac90f526
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410548"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>Nasıl yapılır: Bir Nesnenin Üyelerine Erişme (Visual Basic)

Bir nesneye başvuran bir nesne değişkeniniz varsa, genellikle bu nesnenin, yöntemleri, özellikleri, alanları ve olayları gibi üyeleriyle çalışmak istersiniz. Örneğin, yeni bir nesne oluşturduktan sonra <xref:System.Windows.Forms.Form> , <xref:System.Windows.Forms.Control.Text%2A> özelliğini ayarlamak veya metodunu çağırmak isteyebilirsiniz <xref:System.Windows.Forms.Control.Focus%2A> .

## <a name="accessing-members"></a>Üyelere erişme

Bir nesnenin üyelerine, ona başvuran değişken aracılığıyla erişirsiniz.

#### <a name="to-access-members-of-an-object"></a>Bir nesnenin üyelerine erişmek için

- `.`Nesne değişkeni adı ve üye adı arasındaki üye erişim işlecini () kullanın.

    ```vb
    currentText = newForm.Text
    ```

    Üye [paylaşılmışsa](../../../language-reference/modifiers/shared.md), ona erişmek için bir değişkene ihtiyacınız yoktur.

## <a name="accessing-members-of-an-object-of-known-type"></a>Bilinen türdeki bir nesnenin üyelerine erişme

Derleme zamanında bir nesnenin türünü biliyorsanız, ona başvuran bir değişken için *erken bağlamayı* kullanabilirsiniz.

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>Derleme zamanında türünü bildiğiniz bir nesnenin üyelerine erişmek için

1. Değişkene atamak istediğiniz nesnenin türünün nesne değişkenini bildirin.

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    İle `Option Strict On` , yalnızca <xref:System.Windows.Forms.Form> nesneleri (veya öğesinden türetilmiş bir türün nesnelerini <xref:System.Windows.Forms.Form> ) atayabilirsiniz `extraForm` . Üzerinde genişleyen dönüştürmeye sahip bir sınıf veya yapı tanımladıysanız `CType` <xref:System.Windows.Forms.Form> , bu sınıfa veya yapıya de atayabilirsiniz `extraForm` .

2. `.`Nesne değişkeni adı ve üye adı arasındaki üye erişim işlecini () kullanın.

    ```vb
    extraForm.Show()
    ```

    Ayarın ne olduğuna bakılmaksızın sınıfa özgü tüm yöntemlere ve özelliklere erişebilirsiniz <xref:System.Windows.Forms.Form> `Option Strict` .

## <a name="accessing-members-of-an-object-of-unknown-type"></a>Bilinmeyen türdeki bir nesnenin üyelerine erişme

Derleme zamanında bir nesnenin türünü bilmiyor değilseniz, ona başvuran herhangi bir değişken için *geç bağlamayı* kullanmanız gerekir.

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>Derleme zamanında türünü tanımadığınız bir nesnenin üyelerine erişmek için

1. Nesne [veri türünde](../../../language-reference/data-types/object-data-type.md)olacak nesne değişkenini bildirin. (Bir değişkeni olarak bildirmek ile aynı şekilde bildirme `Object` <xref:System.Object?displayProperty=nameWithType> .)

    ```vb
    Dim someControl As Object
    ```

    İle `Option Strict On` , yalnızca sınıfında tanımlanmış üyelere erişebilirsiniz <xref:System.Object> .

2. `.`Nesne değişkeni adı ve üye adı arasındaki üye erişim işlecini () kullanın.

    ```vb
    someControl.GetType()
    ```

    Nesne değişkenine atadığınız herhangi bir nesnenin üyelerine erişebilmek için, öğesini ayarlamanız gerekir `Option Strict Off` . Bunu yaptığınızda derleyici, belirli bir üyenin değişkene atadığınız nesne tarafından açığa çıkarılabileceği garantisi vermez. Nesne, erişmeye çalıştığınız bir üyeyi kullanıma sunmadığından, bir <xref:System.MemberAccessException> özel durum oluşur.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [Nesne Değişkenleri](object-variables.md)
- [Nesne Değişken Bildirimi](object-variable-declaration.md)
- [Nesne Veri Türü](../../../language-reference/data-types/object-data-type.md)
- [Option Strict Deyimi](../../../language-reference/statements/option-strict-statement.md)
