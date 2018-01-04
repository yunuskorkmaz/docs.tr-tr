---
title: "Nasıl yapılır: .NET Framework Akışları ile Windows Çalışma Zamanı Akışları Arasında Dönüştürme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d9e4c1c0b432ff44af0410b1efdc3940cd0ff19c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-convert-between-net-framework-streams-and-windows-runtime-streams"></a>Nasıl yapılır: .NET Framework Akışları ile Windows Çalışma Zamanı Akışları Arasında Dönüştürme
Windows Mağazası için .NET Framework uygulamaları tam .NET Framework'ün bir alt kümesidir. Windows Mağazası uygulamaları için güvenlik ve diğer gereksinimler nedeniyle, .NET Framework API'ların tam kümesini dosyaları açmak ve okumak için kullanamazsınız. Daha fazla bilgi için bkz: [.NET için Windows mağazası uygulamalarına genel bakış](http://msdn.microsoft.com/library/windows/apps/br230302.aspx). Ancak, diğer akış işleme işlemlerini için .NET Framework API'ları kullanmak isteyebilirsiniz. Bu akışlar işlemek için bu gibi bir .NET Framework akış türü arasında dönüştürme için gerekli bulabilirsiniz <xref:System.IO.MemoryStream> veya <xref:System.IO.FileStream>ve Windows çalışma zamanı akış gibi [IInputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.iinputstream.aspx), [IOutputStream ](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.ioutputstream.aspx), veya [IRandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx).  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions` Sınıfı dönüştürmeler kolaylaştırmak yöntemlerini içerir. Ancak, .NET Framework ve Windows Çalışma Zamanı'nda bu yöntemlerin kullanılmasının sonuçlarını etkileyecek temel farklar vardır. Ayrıtılar aşağıdaki bölümlerde açıklanmıştır.  
  
<a name="BKMK_ConvertingfromaWindowsRuntimestreamtoaNETFrameworkstream"></a>   
## <a name="converting-from-a-windows-runtime-stream-to-a-net-framework-stream"></a>Bir Windows Çalışma Zamanı akışından bir .NET Framework akışına dönüştürme  
 Aşağıdakilerden birini kullanarak bir Windows çalışma zamanı akışından bir .NET Framework akışa dönüştürebilirsiniz <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions` yöntemleri:  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStream`  
 Windows Çalışma Zamanı'ndaki rastgele erişimli bir akışı, Windows Mağazası uygulamaları için .NET alt kümesindeki yönetilen bir akışa dönüştürür.  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite`
 Windows Çalışma Zamanı'ndaki bir çıkış akışını, Windows Mağazası uygulamaları için .NET alt kümesindeki yönetilen bir akışa dönüştürür.  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead`  
 Windows Çalışma Zamanı'ndaki bir giriş akışını, Windows Mağazası uygulamaları için .NET alt kümesindeki yönetilen bir akışa dönüştürür.  
  
 Windows Çalışma Zamanı, yalnızca okumayı, yalnızca yazmayı veya okumayı ve yazmayı destekleyen akış türleri sunar ve bir Windows Çalışma Zamanı akışını bir .NET Framework akışına dönüştürdüğünüzde bu yetenekler korunur. Ayrıca, bir Windows Çalışma Zamanı akışını bir .NET Framework akışına ve sonra geriye dönüştürürseniz, özgün Windows Çalışma Zamanı örneğini geri alırsınız. Dönüştürmek istediğiniz Windows Çalışma Zamanı akışının yetenekleriyle eşleşen dönüştürme yöntemini kullanmak en iyi uygulamadır. Ancak, bu yana [IRandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx) okunabilir ve yazılabilir (her ikisi de uygulayan [IOutputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.ioutputstream.aspx) ve [IInputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.iinputstream.aspx)), dönüştürme yöntemlerden herhangi birini kullanabilirsiniz ve özgün akış özelliklerini saklanır. Örneğin, kullanarak <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead` dönüştürmek için bir [IRandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx) yalnızca okunabilir olması için dönüştürülmüş .NET Framework akışını sınırlandırmak değil; Bu da yazılabilir olacaktır.  
  
#### <a name="to-convert-from-a-windows-runtime-random-access-stream-to-a-net-framework-stream"></a>Bir Windows Çalışma Zamanı rastgele erişimli akışından bir .NET Framework akışına dönüştürmek için  
  
-   Kullanım <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStream` yöntemi.  
  
     Aşağıdaki kod örneğinde, bir kullanıcıdan bir dosya seçmesinin, dosyayı Windows Çalışma Zamanı API'ları ile açmasının ve sonra dosyayı okunan ve bir metin bloğuna çıkışı yapılan bir .NET Framework akışına dönüştürmesinin nasıl isteneceği gösterilmektedir. Bu senaryoda, sonuçların çıktısını almadan önce, genellikle akışı .NET Framework API'ları ile akış işlersiniz.  
  
     Bu örneği çalıştırmak için adlı bir metin bloğunu içeren bir Windows mağazası XAML uygulaması oluşturma `TextBlock1` adlı bir düğmeyi ve `Button1`. Düğmesini tıklatın olay ilişkilendirilmiş, ile `button1_Click` örnekte gösterilen yöntemi.  
  
     [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
     [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]  
    [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#1)]
    [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#1)]  
  
<a name="BKMK_ConvertingfromaNETFrameworkstreamtoaWindowsRuntimestream"></a>   
## <a name="converting-from-a-net-framework-stream-to-a-windows-runtime-stream"></a>Bir .NET Framework akışından bir Windows Çalışma Zamanı akışına dönüştürme  
 Aşağıdakilerden birini kullanarak bir Windows çalışma zamanı akış için .NET Framework akıştan dönüştürebilirsiniz <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions` yöntemleri:  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsInputStream`  
 Windows Mağazası uygulamaları için .NET altkümesindeki yönetilen bir akışı, Windows Çalışma Zamanı'ndaki bir giriş akışına dönüştürür.  
  
<!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsOutputStream%2A>  --> `System.IO.WindowsRuntimeStreamExtensions.AsOutputStream`
 Windows Mağazası uygulamaları için .NET altkümesindeki yönetilen bir akışı, Windows Çalışma Zamanı'ndaki bir çıkış akışına dönüştürür.  
  
 [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md)  
 Windows Mağazası uygulamaları altkümesindeki yönetilen bir akışı, Windows Çalışma Zamanı'nda okuma veya yazma için kullanılabilecek bir rastgele erişim akışına dönüştürür.  
  
 Bir .NET Framework akışını bir Windows Çalışma Zamanı akışına dönüştürdüğünüzde, dönüştürülen akışın yetenekleri özgün akışa bağlı olacaktır. Örneğin özgün akış hem okuma ve yazmayı destekler ve çağırmanız <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsInputStream` akış dönüştürmek için döndürülen tür olacaktır bir `IRandomAccessStream`, hangi uygulayan `IInputStream` ve `IOutputStream`ve okuma destekler ve yazma  
  
 .NET Framework akışları, dönüştürmeden sonra bile klonlamayı desteklemez. Windows çalışma zamanı akış ve arama için bir .NET Framework akış dönüştürürseniz, yani [GetInputStreamAt](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.inmemoryrandomaccessstream.getinputstreamat.aspx) veya [GetOutputStreamAt](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.getoutputstreamat.aspx), hangi çağrısı [CloneStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstreamoverstream.clonestream.aspx) veya arayın [CloneStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstreamoverstream.clonestream.aspx) doğrudan bir özel durum meydana gelir.  
  
#### <a name="to-convert-from-a-net-framework-stream-to-a-windows-runtime-random-access-stream"></a>Bir .NET Framework akışından bir Windows Çalışma Zamanı rastgele erişim akışına dönüştürmek için  
  
-   Kullanım [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) aşağıdaki örnekte gösterildiği gibi yöntemi.  
  
    > [!IMPORTANT]
    >  Kullanmakta olduğunuz .NET Framework akışının aramayı desteklediğinden emin olun veya onu destekleyen bir akışa kopyalayın. Kullanabileceğiniz <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> bunu belirlemek için özellik.  
  
     Bu örneği çalıştırmak için .NET Framework 4.5.1'deki hedefler ve adlı bir metin bloğunu içeren bir Windows mağazası XAML uygulaması oluşturma `TextBlock2` adlı bir düğmeyi ve `Button2`. Düğmesini tıklatın olay ilişkilendirilmiş, ile `button2_Click` Bu örnekte gösterilen yöntemi.  
  
     [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
     [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]  
    [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#2)]
    [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hızlı Başlangıç: Okuma ve yazma dosyası (Windows)](http://msdn.microsoft.com/library/windows/apps/hh464978.aspx)  
 [.NET için Windows mağazası uygulamalarına genel bakış](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 [.NET için Windows mağazası uygulamaları – desteklenen API'leri](http://msdn.microsoft.com/library/windows/apps/br230232.aspx)
