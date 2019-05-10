---
title: 'Nasıl yapılır: CLS Olmayan Özel Durum Değerlendirme'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 27b36d85b2ece957c8ef3fce70a6fd794bb3d4e2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595661"
---
# <a name="how-to-catch-a-non-cls-exception"></a>Nasıl yapılır: CLS Olmayan Özel Durum Değerlendirme
Dahil olmak üzere bazı .NET dilleri C++/CLI, öğesinden türetilen değil özel durumlar oluşturan nesneleri izin <xref:System.Exception>. Bu tür özel durumların adlı *CLS olmayan özel durumları* veya *olmayan özel durumları*. C# ' de CLS olmayan özel durumları oluşturulamıyor, ancak iki yolla yakalayabilir:  
  
- İçinde bir `catch (RuntimeWrappedException e)` blok.
  
     Varsayılan olarak, bir Visual C# Derleme CLS olmayan özel durumlar sarmalanmış özel durumu yakalar. Üzerinden erişilen özgün özel erişime ihtiyacınız varsa, bu yöntemi kullanın <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> özelliği. Bu konunun devamındaki yordamı, bu şekilde özel durumları yakalamak açıklanmaktadır.  
  
- Genel bir catch bloğu (bir catch bloğu olmadan bir özel durum türü belirtilmiş) içinde yerleştirildiğini sonra diğer tüm `catch` engeller.
  
     Yanıt olarak CLS olmayan özel durumları (örneğin, bir günlük dosyasına yazma) bir eylem gerçekleştirmek istediğiniz ve özel durum bilgilerine erişim gerekmez, bu yöntemi kullanın. Varsayılan olarak, tüm özel durumları ortak dil çalışma zamanı sarmalar. Bu davranışı devre dışı bırakmak için genellikle AssemblyInfo.cs dosyasında kodunuzda bu derleme düzeyi özniteliğini ekleyin: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.  
  
### <a name="to-catch-a-non-cls-exception"></a>CLS olmayan özel durum yakalamak için  
  
İçinde bir `catch(RuntimeWrappedException e)` engelleme, özgün özel durum aracılığıyla erişim <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, C +'da yazılmış bir sınıf kitaplığından oluşturulan bir CLS olmayan özel durum yakalamak gösterilmektedir +/ CLI. Bu örnekte, C# istemci kodu önceden oluşturulan özel durum türü olduğunu bilir, Not bir <xref:System.String?displayProperty=nameWithType>. Atayabilirsiniz <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> özelliği orijinal türe geri türü kodunuz içinden erişilebilir olduğu sürece.  
  
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
- [Özel Durumlar ve Özel Durum İşleme](../../../csharp/programming-guide/exceptions/index.md)
