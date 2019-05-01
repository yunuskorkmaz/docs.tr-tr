---
title: 'İzlenecek yol: Direct3D9 İçeriğini WPF’de Barındırma'
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: 07cfa5bed6e5af131a60a303f0702f18413043e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007138"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a>İzlenecek yol: Direct3D9 İçeriğini WPF’de Barındırma
Bu izlenecek yol, bir Windows Presentation Foundation (WPF) uygulamasındaki Direct3D9 içeriği barındırma işlemi gösterilmektedir.  
  
 Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:  
  
- Direct3D9 içeriğini barındırmak için bir WPF projesi oluşturun.  
  
- Direct3D9 içeriğini içeri aktarın.  
  
- Direct3D9 içeriğini kullanarak görüntüleyin <xref:System.Windows.Interop.D3DImage> sınıfı.  
  
 İşlemi tamamladığınızda, bir WPF uygulamasında Direct3D9 içeriğini barındırmak nasıl atayacağınızı biliyor olacaksınız.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
- Visual Studio.  
  
- DirectX SDK 9 veya üzeri.  
  
- WPF ile uyumlu bir biçimde Direct3D9 içeriği içeren bir DLL. Daha fazla bilgi için [WPF ve Direct3D9 birlikte çalışması](wpf-and-direct3d9-interoperation.md) ve [izlenecek yol: WPF'de barındırmak için Direct3D9 içeriği oluşturma](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
## <a name="creating-the-wpf-project"></a>WPF projesi oluşturma  
 İlk adım WPF uygulaması için proje oluşturmaktır.  
  
#### <a name="to-create-the-wpf-project"></a>WPF projesini oluşturmak için  
  
- Visual C# ' adlı yeni bir WPF uygulaması projesi oluşturma `D3DHost`. Daha fazla bilgi için [izlenecek yol: İlk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
     MainWindow.xaml açılır [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
## <a name="importing-the-direct3d9-content"></a>Direct3D9 içeriğini alma  
 Direct3D9 içeriğini kullanarak yönetilmeyen DLL dosyasından içeri `DllImport` özniteliği.  
  
#### <a name="to-import-direct3d9-content"></a>Direct3D9 içeriğini içeri aktarmak için  
  
1. Kod Düzenleyicisi'nde MainWindow.xaml.cs dosyasını açın.  
  
2. Otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a>Direct3D9 içeriği barındırma  
 Son olarak, <xref:System.Windows.Interop.D3DImage> Direct3D9 içeriğini barındırmak için sınıf.  
  
#### <a name="to-host-the-direct3d9-content"></a>Direct3D9 içeriğini barındırmak için  
  
1. MainWindow.xaml içinde otomatik olarak oluşturulan XAML aşağıdaki XAML ile değiştirin.  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2. Projeyi oluşturun.  
  
3. Direct3D9 içeriği bin/Debug klasörüne içeren DLL kopyalayın.  
  
4. Projeyi çalıştırmak için F5 tuşuna basın.  
  
     Direct3D9 içeriği WPF uygulaması içinde görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.D3DImage>
- [Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
