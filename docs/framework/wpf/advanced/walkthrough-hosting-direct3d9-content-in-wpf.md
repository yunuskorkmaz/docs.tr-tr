---
title: "İzlenecek yol: WPF'de Direct3D9 İçeriği Barındırma"
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: 3b215c0eead8c5fc28b477b81f75c39b5c946302
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546178"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a>İzlenecek yol: WPF'de Direct3D9 İçeriği Barındırma
Bu kılavuz, bir Windows Presentation Foundation (WPF) uygulamasında Direct3D9 içeriğini barındırmak gösterilmiştir.  
  
 Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:  
  
-   Direct3D9 içeriğini barındırmak için bir WPF projesi oluşturun.  
  
-   Direct3D9 içeriğini içeri aktarın.  
  
-   Kullanarak Direct3D9 içeriğini görüntüleyin <xref:System.Windows.Interop.D3DImage> sınıfı.  
  
 İşiniz bittiğinde, bir WPF uygulamasında Direct3D9 içeriğini barındırmak nasıl anlarsınız.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   DirectX SDK 9 veya üzeri.  
  
-   WPF ile uyumlu bir biçimde Direct3D9 içeriği içeren bir DLL. Daha fazla bilgi için bkz: [WPF ve Direct3D9 birlikte çalışma](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) ve [izlenecek yol: oluşturma Direct3D9 içeriği WPF içinde barındırma](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
## <a name="creating-the-wpf-project"></a>WPF projesi oluşturma  
 İlk adım WPF uygulaması için projeyi oluşturmaktır.  
  
#### <a name="to-create-the-wpf-project"></a>WPF projesini oluşturmak için  
  
-   Visual C# ' adlı yeni bir WPF uygulaması projesi oluşturma `D3DHost`. Daha fazla bilgi için bkz: [nasıl yapılır: yeni bir WPF uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
     MainWindow.xaml açılır [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
## <a name="importing-the-direct3d9-content"></a>Direct3D9 içeriğini alma  
 Kullanarak yönetilmeyen DLL dosyasından Direct3D9 içeriğini içeri `DllImport` özniteliği.  
  
#### <a name="to-import-direct3d9-content"></a>Direct3D9 içeriğini içeri aktarmak için  
  
1.  MainWindow.xaml.cs kod düzenleyicisinde açın.  
  
2.  Otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a>Direct3D9 içeriği barındırma  
 Son olarak, <xref:System.Windows.Interop.D3DImage> Direct3D9 içeriğini barındırmak için sınıf.  
  
#### <a name="to-host-the-direct3d9-content"></a>Direct3D9 içeriğini barındırmak için  
  
1.  MainWindow.xaml içinde otomatik olarak oluşturulan XAML aşağıdaki XAML ile değiştirin.  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  Projeyi oluşturun.  
  
3.  Bin/Debug klasörüne Direct3D9 içeriği DLL kopyalayın.  
  
4.  Projeyi çalıştırmak için F5 tuşuna basın.  
  
     Direct3D9 içeriği WPF uygulaması içinde görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Interop.D3DImage>  
 [Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
