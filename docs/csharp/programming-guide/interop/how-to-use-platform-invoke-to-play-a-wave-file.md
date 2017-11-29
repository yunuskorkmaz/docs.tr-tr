---
title: "Nasıl yapılır: Wave Dosyasını Oynatmak için Platform Çağırma Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d037e17ef48ebfdd5cfd860efbacf195e7b6a76d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a>Nasıl yapılır: Wave Dosyasını Oynatmak için Platform Çağırma Kullanma (C# Programlama Kılavuzu)
Aşağıdaki C# kod örneğinde nasıl platform kullanılacağını anlatan Windows işletim sisteminde ses wave dosyasını oynatmak için hizmetlerini çağırma.  
  
## <a name="example"></a>Örnek  
 Bu kod örneği kullanan `DllImport` almak için `winmm.dll`'s `PlaySound` yöntemi giriş noktası olarak `Form1 PlaySound()`. Örnek basit bir Windows formunda bir düğme vardır. Düğmesine tıkladığınızda açılır standart windows <xref:System.Windows.Forms.OpenFileDialog> iletişim kutusunu yürütmek için bir dosyayı açın. Wave dosyasını seçildiğinde kullanarak çalınır `PlaySound()` WINMM yöntemi. DLL derleme yöntemi. Winmm.dll'ın hakkında daha fazla bilgi için `PlaySound` yöntemi, bkz: [dalga biçiminin ses dosyaları ile PlaySound işlevini kullanarak](http://go.microsoft.com/fwlink/?LinkId=148553). Gözat ve .wav uzantılı bir dosya seçin ve ardından **açık** oynatmak için platform kullanarak wave dosyasını çağırır. Bir metin kutusu seçili dosyasının tam yolunu gösterir.  
  
 **Açık dosyalar** iletişim kutusu filtre filtre ayarları aracılığıyla .wav uzantısı olan dosyaları göstermek için:  
  
 [!code-csharp[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-csharp[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
### <a name="to-compile-the-code"></a>Kodu derlemek için  
  
1.  Visual Studio'da yeni bir C# Windows uygulama projesi oluşturun ve adlandırın **WinSound**.  
  
2.  Yukarıdaki kodu kopyalayabilir ve üzerinde içeriğini yapıştırın `Form1.cs` dosya.  
  
3.  Aşağıdaki kodu kopyalayın ve yapıştırın `Form1.Designer.cs` dosyasında `InitializeComponent()` tüm var olan koddan sonra yöntemi.  
  
     [!code-csharp[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  Derleme ve kodu çalıştırın.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Daha fazla bilgi için bkz: [.NET Framework Güvenliği](http://go.microsoft.com/fwlink/?LinkId=37122).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Birlikte çalışabilirliğe genel bakış](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [Birlikte çalışabilirliğe genel bakış](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [Yakından Platform çağırma](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [Platform Çağırma ile veri hazırlama](../../../framework/interop/marshaling-data-with-platform-invoke.md)
