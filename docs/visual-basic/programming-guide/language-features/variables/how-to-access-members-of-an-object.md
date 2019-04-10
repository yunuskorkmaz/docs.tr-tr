---
title: 'Nasıl yapılır: Erişim üyeleri bir nesnenin (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: de00e428cc3d9d7a5688e853b0ff4295fec5b3e9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322764"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>Nasıl yapılır: Erişim üyeleri bir nesnenin (Visual Basic)
Bir nesneye başvuruda bulunan bir nesne değişkeni varsa, genellikle o nesnenin yöntemler, özellikler, alanlar ve olaylar gibi üyeleri birlikte çalışmak istediğiniz. Örneğin, bir kez oluşturduğunuz yeni bir <xref:System.Windows.Forms.Form> nesne ayarlamak isteyebilirsiniz, <xref:System.Windows.Forms.Control.Text%2A> özelliği veya çağrı kendi <xref:System.Windows.Forms.Control.Focus%2A> yöntemi.  
  
## <a name="accessing-members"></a>Üyelere erişme  
 Bir nesnenin üyeleri, ona başvuran değişkeni aracılığıyla erişin.  
  
#### <a name="to-access-members-of-an-object"></a>Bir nesnenin üyelerine erişmek için  
  
-   Üye erişimi işlecini kullanın (`.`) üye adı arasındaki nesne değişkeni adı.  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     Üye [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md), ona erişmek için bir değişken gerekmez.  
  
## <a name="accessing-members-of-an-object-of-known-type"></a>Bilinen türünde bir nesnenin üyelerine erişme  
 Derleme zamanında bir nesne türünü biliyorsanız, kullanabileceğiniz *erken bağlama* kendisine başvuran bir değişken için.  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>Derleme zamanında tür öğrenmek bildiğiniz bir nesnenin üyelerine erişmek için  
  
1. Değişkenine atamak istediğiniz nesne türünü olmaya nesne değişkeni bildirme.  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     İle `Option Strict On`, yalnızca atayabilirsiniz <xref:System.Windows.Forms.Form> nesneleri (veya bir türden nesneleri türetilen <xref:System.Windows.Forms.Form>) için `extraForm`. Bir sınıf veya yapı bir genişletme ile tanımlanan, `CType` dönüştürme <xref:System.Windows.Forms.Form>, ayrıca bu sınıf atayın veya için yapı `extraForm`.  
  
2. Üye erişimi işlecini kullanın (`.`) üye adı arasındaki nesne değişkeni adı.  
  
    ```  
    extraForm.Show()  
    ```  
  
     Tüm yöntemler ve özellikler için belirli erişebileceğiniz <xref:System.Windows.Forms.Form> ne olursa olsun, sınıf `Option Strict` ayardır.  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a>Bilinmeyen türdeki bir nesnenin üyelerine erişme  
 Derleme zamanında bir nesnenin türünü bilmiyorsanız kullanmalısınız *geç bağlama* kendisine başvuran herhangi bir değişken için.  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>Kendisi için türü derleme zamanında bilmediğiniz bir nesnenin üyelerine erişmek için  
  
1. Olmaya nesne değişkeni bildirme [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md). (Bir değişken olarak bildirme `Object` olarak bildirme aynı <xref:System.Object?displayProperty=nameWithType>.)  
  
    ```  
    Dim someControl As Object  
    ```  
  
     İle `Option Strict On`, üzerinde tanımlanan üyeler erişebileceğiniz <xref:System.Object> sınıfı.  
  
2. Üye erişimi işlecini kullanın (`.`) üye adı arasındaki nesne değişkeni adı.  
  
    ```  
    someControl.GetType()  
    ```  
  
     Nesne değişkenine atayın herhangi bir nesnenin üyeleri erişebilmesi için ayarlamalısınız `Option Strict Off`. Bunu yaptığınızda, derleyici belirli bir üye değişkenine atayın nesnesi tarafından kullanıma sunulduğunu garanti edemez. Nesne girişiminde erişmek için üye sunmuyorsa bir <xref:System.MemberAccessException> özel durum oluşur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Nesne Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
