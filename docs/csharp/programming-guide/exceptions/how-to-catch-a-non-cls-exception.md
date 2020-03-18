---
title: CLS dışı özel durumu yakalama
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 635cf0a9142f56dea4b2722fbf3f3eda505d85ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75346272"
---
# <a name="how-to-catch-a-non-cls-exception"></a>CLS dışı özel durumu yakalama
C++/CLI dahil olmak üzere bazı .NET dilleri, nesnelerin <xref:System.Exception>. Bu tür özel *durumlar, CLS dışı özel durumlar* veya Özel Durumlar *olarak*adlandırılır. C#'da CLS dışı özel durumlar atamazsınız, ancak bunları iki şekilde yakalayabilirsiniz:  
  
- Bir `catch (RuntimeWrappedException e)` blok içinde.
  
     Varsayılan olarak, Visual C# derlemesi CLS olmayan özel durumları sarılmış özel durumlar olarak yakalar. <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> Özellik üzerinden erişilebilen özgün özel durum özelliğine erişmeniz gerekiyorsa bu yöntemi kullanın. Bu konunun ilerleyen sonraki yordamı, özel durumların bu şekilde nasıl yakaılacağını açıklar.  
  
- Genel bir catch bloğu içinde (bir istisna türü belirtilmeden bir `catch` catch blok) tüm diğer bloklar sonra konur.
  
     CLS dışı özel durumlara yanıt olarak bazı eylem (günlük dosyasına yazma gibi) gerçekleştirmek istediğinizde bu yöntemi kullanın ve özel durum bilgilerine erişmeniz gerekmez. Varsayılan olarak ortak dil çalışma süresi tüm özel durumları sarar. Bu davranışı devre dışı katmak için, genellikle AssemblyInfo.cs dosyasında bu derleme `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`düzeyi özniteliğini kodunuza ekleyin: .  
  
### <a name="to-catch-a-non-cls-exception"></a>CLS olmayan bir özel durum yakalamak için  
  
Bir `catch(RuntimeWrappedException e)` blok içinde, özellik üzerinden <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> orijinal özel durum erişin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, C++/CLI ile yazılmış bir sınıf kitaplığından atılan CLS olmayan bir özel durum nasıl yakalandığını gösterir. Bu örnekte, C# istemci kodu atılan özel durum türünün <xref:System.String?displayProperty=nameWithType>bir . olduğunu önceden bildiğini unutmayın Bu türe <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> kodunuzdan erişilebildiği sürece özelliği özgün türünü geri atabilirsiniz.  
  
```csharp
// Class library written in C++/CLI.
var myClass = new ThrowNonCLS.Class1();

try
{
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();
}
catch (RuntimeWrappedException e)
{
    String s = e.WrappedException as String;
    if (s != null)
    {
        Console.WriteLine(s);
    }
}
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [Özel Durumlar ve Özel Durum Kullanımı](./index.md)
