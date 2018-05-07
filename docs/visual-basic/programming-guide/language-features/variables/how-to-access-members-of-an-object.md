---
title: 'Nasıl yapılır: Bir Nesnenin Üyelerine Erişme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 62be2955bd1f62fa5af4e54fb0af5e7dca29c421
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>Nasıl yapılır: Bir Nesnenin Üyelerine Erişme (Visual Basic)
Bir nesneye başvuruda bulunan bir nesne değişkeni varsa, genellikle yöntemler, özellikler, alanları ve olaylar gibi söz konusu nesne üyeleri çalışmak istediğiniz. Örneğin, bir kez oluşturduğunuz yeni bir <xref:System.Windows.Forms.Form> nesne ayarlamak isteyebilirsiniz, <xref:System.Windows.Forms.Control.Text%2A> özelliği veya çağrı kendi <xref:System.Windows.Forms.Control.Focus%2A> yöntemi.  
  
## <a name="accessing-members"></a>Üyelere erişme  
 Kendisine başvuran değişkeni aracılığıyla bir nesnenin üyeleri erişin.  
  
#### <a name="to-access-members-of-an-object"></a>Bir nesnenin üyelerine erişmek için  
  
-   Üye erişimi işleci kullanın (`.`) arasında nesne değişken adını ve üye adı.  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     Üye ise [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md), erişmek için bir değişken gerekmez.  
  
## <a name="accessing-members-of-an-object-of-known-type"></a>Bilinen türünde bir nesnenin üyelerine erişme  
 Derleme zamanında bir nesne türünü biliyorsanız, kullanabileceğiniz *erken bağlama* kendisine başvuran bir değişken için.  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>Derleme zamanında türü öğrenmek bildiğiniz bir nesnenin üyelerine erişmek için  
  
1.  Değişkenine atamak istediğiniz nesne türünü olmaya nesne değişkeni bildirme.  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     İle `Option Strict On`, yalnızca atayabilirsiniz <xref:System.Windows.Forms.Form> nesneler (veya bir türdeki nesneleri türetilen <xref:System.Windows.Forms.Form>) için `extraForm`. Bir sınıf veya yapı bir genişletme ile tanımlanan, `CType` dönüştürme <xref:System.Windows.Forms.Form>, ayrıca bu sınıf atayın veya için yapı `extraForm`.  
  
2.  Üye erişimi işleci kullanın (`.`) arasında nesne değişken adını ve üye adı.  
  
    ```  
    extraForm.Show()  
    ```  
  
     Tüm özgü özellikleri ve yöntemleri erişebilirsiniz <xref:System.Windows.Forms.Form> ne olursa olsun sınıfı `Option Strict` ayardır.  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a>Bilinmeyen türdeki bir nesnenin üyelerine erişme  
 Derleme zamanında bir nesnenin türünü bilmiyorsanız, kullanmalısınız *geç bağlama* kendisine başvuran herhangi bir değişken için.  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>Kendisi için türü derleme zamanında Tanımadığınız bir nesnenin üyelerine erişmek için  
  
1.  Olmaya nesne değişkeni bildirme [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md). (Bir değişken olarak bildirme `Object` olarak bildirme aynı <xref:System.Object?displayProperty=nameWithType>.)  
  
    ```  
    Dim someControl As Object  
    ```  
  
     İle `Option Strict On`, üzerinde tanımlanan üyeleri erişebilir <xref:System.Object> sınıfı.  
  
2.  Üye erişimi işleci kullanın (`.`) arasında nesne değişken adını ve üye adı.  
  
    ```  
    someControl.GetType()  
    ```  
  
     Nesne değişkeni atadığınız herhangi bir nesnenin üyelerine erişebilmeleri için ayarlamalısınız `Option Strict Off`. Bunu yaptığınızda derleyici belirli bir üye değişkenine atayın nesnesi tarafından sunulan garanti edemez. Nesne erişim çalıştığınızda üye imkanı sunmuyorsa bir <xref:System.MemberAccessException> özel durum oluştu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Object>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.MemberAccessException>  
 [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Nesne Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
