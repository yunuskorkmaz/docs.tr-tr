---
title: 'Nasıl yapılır: CLS Olmayan Özel Durum Değerlendirme'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
caps.latest.revision: 8
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5647fc8501afe2a4bf74739fd8efd4e6b74559a2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-catch-a-non-cls-exception"></a>Nasıl yapılır: CLS Olmayan Özel Durum Değerlendirme
C + dahil olmak üzere bazı .NET dillerini +/ CLI, nesnelerin öğesinden türetilen olmayan özel durumlar oluşturma izin <xref:System.Exception>. Bu tür özel durumlar olarak adlandırılan *CLS olmayan özel durumları* veya *özel durumları olmayan*. Visual C# ' CLS olmayan özel durumları atılamıyor, ancak iki yolla catch:  
  
-   İçinde bir `catch (Exception e)` olarak engelleme bir <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  
  
     Varsayılan olarak, bir Visual C# derleme Sarmalanan özel durumlar olarak CLS olmayan özel durumları yakalar. Üzerinden erişilen özgün özel erişmesi gerekiyorsa bu yöntemi kullanın <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> özelliği. Bu konunun devamındaki yordamı bu şekilde özel durumlarını yakalama açıklanmaktadır.  
  
-   Bir genel catch bloğu (catch bloğu bir özel durum türü belirtilmiş olmadan) içinde put sonra bir `catch (Exception)` veya `catch (Exception e)` bloğu.  
  
     Özel durum bilgilerini erişimi gerekmez ve yanıt CLS olmayan özel durumlar olarak (örneğin, bir günlük dosyasına yazılırken) bazı eylemler gerçekleştirme istediğinizde bu yöntemi kullanın. Varsayılan olarak, tüm özel durumları ortak dil çalışma zamanı sarmalar. Bu davranışı devre dışı bırakmak için genellikle AssemblyInfo.cs dosyasında kodunuzu bu derleme düzeyi özniteliğini ekleyin: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.  
  
### <a name="to-catch-a-non-cls-exception"></a>CLS olmayan özel durumu yakalamak için  
  
1.  İçinde bir `catch(Exception e) block`, kullanın `as` test etmek için anahtar sözcüğü olup olmadığını `e` atanabilecek bir <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  
  
2.  Orijinal özel durumu ile erişim <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte yazılan C + sınıf kitaplığı'ndan oluşturulan bir CLS olmayan özel catch gösterilmektedir +/ CLR. Bu örnekte, Visual C# istemci kodu önceden oluşturulan özel durum türü olduğunu bilir olduğunu unutmayın bir <xref:System.String?displayProperty=nameWithType>. Cast <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> özellik türü kodunuzdan erişilebilir olduğu sürece özgün türüne yedekleyin.  
  
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
 [Özel Durumlar ve Özel Durum İşleme](../../../csharp/programming-guide/exceptions/index.md)
