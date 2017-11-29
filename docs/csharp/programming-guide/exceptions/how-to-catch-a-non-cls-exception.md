---
title: "Nasıl yapılır: CLS Olmayan Özel Durum Değerlendirme"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 473cace033983915c66647d14cae16dc7f5d5b9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-catch-a-non-cls-exception"></a>Nasıl yapılır: CLS Olmayan Özel Durum Değerlendirme
C + dahil olmak üzere bazı .NET dillerini +/ CLI, nesnelerin öğesinden türetilen olmayan özel durumlar oluşturma izin <xref:System.Exception>. Bu tür özel durumlar olarak adlandırılan *CLS olmayan özel durumları* veya *özel durumları olmayan*. İçinde [!INCLUDE[csprcs](~/includes/csprcs-md.md)] CLS olmayan özel durumlar oluşturma olamaz, ancak iki yolla catch:  
  
-   İçinde bir `catch (Exception e)` olarak engelleme bir <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  
  
     Varsayılan olarak, bir [!INCLUDE[csprcs](~/includes/csprcs-md.md)] derleme Sarmalanan özel durumlar olarak CLS olmayan özel durumları yakalar. Üzerinden erişilen özgün özel erişmesi gerekiyorsa bu yöntemi kullanın <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> özelliği. Bu konunun devamındaki yordamı bu şekilde özel durumlarını yakalama açıklanmaktadır.  
  
-   Bir genel catch bloğu (catch bloğu bir özel durum türü belirtilmiş olmadan) içinde put sonra bir `catch (Exception)` veya `catch (Exception e)` bloğu.  
  
     Özel durum bilgilerini erişimi gerekmez ve yanıt CLS olmayan özel durumlar olarak (örneğin, bir günlük dosyasına yazılırken) bazı eylemler gerçekleştirme istediğinizde bu yöntemi kullanın. Varsayılan olarak, tüm özel durumları ortak dil çalışma zamanı sarmalar. Bu davranışı devre dışı bırakmak için genellikle AssemblyInfo.cs dosyasında kodunuzu bu derleme düzeyi özniteliğini ekleyin: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.  
  
### <a name="to-catch-a-non-cls-exception"></a>CLS olmayan özel durumu yakalamak için  
  
1.  İçinde bir `catch(Exception e) block`, kullanın `as` test etmek için anahtar sözcüğü olup olmadığını `e` atanabilecek bir <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  
  
2.  Orijinal özel durumu ile erişim <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte yazılan C + sınıf kitaplığı'ndan oluşturulan bir CLS olmayan özel catch gösterilmektedir +/ CLR. Bu örnekte, unutmayın [!INCLUDE[csprcs](~/includes/csprcs-md.md)] oluşturulan özel durum türü olduğunu istemci kodu önceden bildiği bir <xref:System.String?displayProperty=nameWithType>. Cast <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> özellik türü kodunuzdan erişilebilir olduğu sürece özgün türüne yedekleyin.  
  
```  
// Class library written in C++/CLR.  
   ThrowNonCLS.Class1 myClass = new ThrowNonCLS.Class1();  
  
   try  
   {  
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();   
   }  
  
   catch (Exception e)  
   {  
    RuntimeWrappedException rwe = e as RuntimeWrappedException;  
    if (rwe != null)      
    {  
      String s = rwe.WrappedException as String;  
      if (s != null)  
      {  
        Console.WriteLine(s);  
      }  
    }  
    else  
    {  
       // Handle other System.Exception types.  
    }  
   }             
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>  
 [Özel durumlar ve özel durum işleme](../../../csharp/programming-guide/exceptions/index.md)
