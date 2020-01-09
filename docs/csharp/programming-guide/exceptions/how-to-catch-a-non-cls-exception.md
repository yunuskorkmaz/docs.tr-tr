---
title: CLS dışı özel durumu yakalama
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 635cf0a9142f56dea4b2722fbf3f3eda505d85ee
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346272"
---
# <a name="how-to-catch-a-non-cls-exception"></a>CLS dışı özel durumu yakalama
/CLI dahil C++bazı .NET dilleri, nesnelerin <xref:System.Exception>türetmeyen özel durumlar oluşturması için izin verir. Bu tür özel durumlar *CLS dışı özel durumlar* veya *özel durumlar*olarak adlandırılır. İçinde C# CLS olmayan özel durumlar belirtemezsiniz, ancak bunları iki şekilde yakalayabilirsiniz:  
  
- `catch (RuntimeWrappedException e)` bloğu içinde.
  
     Varsayılan olarak, bir görsel C# derleme CLS olmayan özel durumları sarmalanmış özel durumlar olarak yakalar. <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> özelliği aracılığıyla erişilebilen özgün özel duruma erişmeniz gerekiyorsa bu yöntemi kullanın. Bu konu başlığında ilerleyen yordamda, özel durumların bu şekilde nasıl yakalanacağı açıklanmaktadır.  
  
- Genel bir catch bloğu içinde (özel durum türü belirtilmeden bir catch bloğu), diğer tüm `catch` bloklarından sonra konur.
  
     CLS olmayan özel durumlara yanıt olarak bazı eylemler (örneğin, bir günlük dosyasına yazma) gerçekleştirmek istediğinizde ve özel durum bilgilerine erişmeniz gerekmiyorsa bu yöntemi kullanın. Varsayılan olarak ortak dil çalışma zamanı tüm özel durumları sarmalanır. Bu davranışı devre dışı bırakmak için, bu derleme düzeyi özniteliğini kodunuza, genellikle AssemblyInfo.cs dosyasında: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`ekleyin.  
  
### <a name="to-catch-a-non-cls-exception"></a>CLS olmayan bir özel durumu yakalamak için  
  
`catch(RuntimeWrappedException e)` bloğu içinde, <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> özelliği aracılığıyla özgün özel duruma erişin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek,/Cliende C++yazılmış bir sınıf KITAPLıĞıNDAN oluşturulan CLS olmayan bir özel durumun nasıl yakalanalınacağını gösterir. Bu örnekte, C# istemci kodunun, oluşturulan özel durum türünün bir <xref:System.String?displayProperty=nameWithType>olduğunu önceden öğrendiğine unutmayın. <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> özelliğini, bu tür kodunuzun erişebileceği sürece özgün türünü geri çevirebilirsiniz.  
  
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
