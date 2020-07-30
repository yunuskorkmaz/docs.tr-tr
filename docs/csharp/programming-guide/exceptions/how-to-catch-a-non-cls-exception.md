---
title: CLS dışı özel durumu yakalama
description: CLS dışı bir özel durum yakalama hakkında bilgi edinin. Bir kod örneğine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 255de4cab9a72491eb3b9624d968539d432e0442
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302015"
---
# <a name="how-to-catch-a-non-cls-exception"></a>CLS dışı özel durumu yakalama
C++/CLı dahil bazı .NET dilleri, nesnelerin türetmeyen özel durumlar oluşturmasını sağlar <xref:System.Exception> . Bu tür özel durumlar *CLS dışı özel durumlar* veya *özel durumlar*olarak adlandırılır. C# dilinde CLS olmayan özel durumlar belirtemezsiniz, ancak bunları iki şekilde yakalayabilirsiniz:  
  
- Bir `catch (RuntimeWrappedException e)` blok içinde.
  
     Varsayılan olarak, bir Visual C# derlemesi, CLS dışı özel durumları sarmalanmış özel durumlar olarak yakalar. Bu yöntemi, özelliği aracılığıyla erişilebilen özgün özel duruma erişmeniz gerekiyorsa kullanın <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> . Bu konu başlığında ilerleyen yordamda, özel durumların bu şekilde nasıl yakalanacağı açıklanmaktadır.  
  
- Genel bir catch bloğu içinde (özel durum türü belirtilmeden bir catch bloğu), diğer tüm bloklarından sonra konur `catch` .
  
     CLS olmayan özel durumlara yanıt olarak bazı eylemler (örneğin, bir günlük dosyasına yazma) gerçekleştirmek istediğinizde ve özel durum bilgilerine erişmeniz gerekmiyorsa bu yöntemi kullanın. Varsayılan olarak ortak dil çalışma zamanı tüm özel durumları sarmalanır. Bu davranışı devre dışı bırakmak için, bu derleme düzeyi özniteliğini kodunuzda, genellikle AssemblyInfo.cs dosyasında ekleyin: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]` .  
  
### <a name="to-catch-a-non-cls-exception"></a>CLS olmayan bir özel durumu yakalamak için  
  
Bir `catch(RuntimeWrappedException e)` blok içinde, özelliği aracılığıyla özgün özel duruma erişin <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, C++/CLIENDE yazılmış bir sınıf kitaplığından oluşturulan CLS olmayan bir özel durumun nasıl yakalanalınacağını gösterir. Bu örnekte, C# istemci kodunun, oluşturulmakta olan özel durum türünün bir olduğunu önceden öğrendiğine unutmayın <xref:System.String?displayProperty=nameWithType> . <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType>Bu tür, kodunuzun erişebileceği sürece özelliği özgün türünü geri çevirebilirsiniz.  
  
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
- [Özel durumlar ve özel durum Işleme](./index.md)
