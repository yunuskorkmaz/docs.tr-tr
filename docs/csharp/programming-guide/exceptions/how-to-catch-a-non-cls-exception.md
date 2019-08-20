---
title: 'Nasıl yapılır: CLS Olmayan Özel Durum Değerlendirme'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: d0ba212610372a89c2a3b4c6a249c6d8a02fa507
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590290"
---
# <a name="how-to-catch-a-non-cls-exception"></a>Nasıl yapılır: CLS Olmayan Özel Durum Değerlendirme
/CLI dahil C++bazı .NET dilleri, nesnelerin türetmeyen <xref:System.Exception>özel durumlar oluşturması için izin verir. Bu tür özel durumlar *CLS dışı özel durumlar* veya *özel durumlar*olarak adlandırılır. İçinde C# CLS olmayan özel durumlar belirtemezsiniz, ancak bunları iki şekilde yakalayabilirsiniz:  
  
- Bir `catch (RuntimeWrappedException e)` blok içinde.
  
     Varsayılan olarak, bir görsel C# derleme CLS olmayan özel durumları sarmalanmış özel durumlar olarak yakalar. Bu yöntemi, <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> özelliği aracılığıyla erişilebilen özgün özel duruma erişmeniz gerekiyorsa kullanın. Bu konu başlığında ilerleyen yordamda, özel durumların bu şekilde nasıl yakalanacağı açıklanmaktadır.  
  
- Genel bir catch bloğu içinde (özel durum türü belirtilmeden bir catch bloğu), diğer `catch` tüm bloklarından sonra konur.
  
     CLS olmayan özel durumlara yanıt olarak bazı eylemler (örneğin, bir günlük dosyasına yazma) gerçekleştirmek istediğinizde ve özel durum bilgilerine erişmeniz gerekmiyorsa bu yöntemi kullanın. Varsayılan olarak ortak dil çalışma zamanı tüm özel durumları sarmalanır. Bu davranışı devre dışı bırakmak için, bu derleme düzeyi özniteliğini kodunuzda, genellikle AssemblyInfo.cs dosyasında ekleyin: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.  
  
### <a name="to-catch-a-non-cls-exception"></a>CLS olmayan bir özel durumu yakalamak için  
  
Bir `catch(RuntimeWrappedException e)` blok içinde, <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> özelliği aracılığıyla özgün özel duruma erişin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek,/Cliende C++yazılmış bir sınıf KITAPLıĞıNDAN oluşturulan CLS olmayan bir özel durumun nasıl yakalanalınacağını gösterir. Bu örnekte, C# istemci kodunun, oluşturulmakta olan özel durum türünün bir <xref:System.String?displayProperty=nameWithType>olduğunu önceden öğrendiğine unutmayın. Bu tür, kodunuzun <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> erişebileceği sürece özelliği özgün türünü geri çevirebilirsiniz.  
  
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
- [Özel Durumlar ve Özel Durum İşleme](./index.md)
