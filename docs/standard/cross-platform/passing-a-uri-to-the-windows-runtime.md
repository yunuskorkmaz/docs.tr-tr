---
title: URI'yı Windows Çalışma Zamanı'na Geçirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a31a1246fe311c36e7457327c79aeeef30e7813
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568842"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>URI'yı Windows Çalışma Zamanı'na Geçirme
Windows çalışma zamanı yöntemleri yalnızca mutlak URI kabul edin. Göreli URI'yı geçirirseniz bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] yöntemi, bir <xref:System.ArgumentException> özel durumu oluşur. Neden şöyledir: kullandığınızda [!INCLUDE[wrt](../../../includes/wrt-md.md)] .NET Framework kodda, <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıfı görünür olarak <xref:System.Uri?displayProperty=nameWithType> IntelliSense içinde. <xref:System.Uri?displayProperty=nameWithType> Sınıfı göreli URI'ler sağlar ancak <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıfı yok. Bu, aynı zamanda, kullanıma yöntemleri için geçerlidir [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşenleri. Bileşeniniz bir URI götüren bir yöntemi gösterir, kodunuzda imza içeren <xref:System.Uri?displayProperty=nameWithType>. Ancak, bileşeniniz kullanıcılara imza içeren <xref:Windows.Foundation.Uri?displayProperty=nameWithType>. Bileşeniniz için geçirilen bir URI mutlak URI olmalıdır.  
  
 Bu konu, bir mutlak URI algılanması ve bir uygulama paketinde bir kaynağa başvuran oluşturduğunuzda gösterir.  
  
## <a name="detecting-and-using-an-absolute-uri"></a>Algılama ve bir mutlak URI kullanma  
 Kullanım <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> geçirmeden önce bir URI mutlak olduğundan emin olmak için özellik [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Bu özellik kullanılarak yakalama ve işleme daha verimli <xref:System.ArgumentException> özel durum.  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>Uygulama paketini bir kaynak için bir mutlak URI kullanma  
 Uygulama paketinizi içeren bir kaynak için bir URI belirtmek istiyorsanız, kullanabileceğiniz `ms-appx` veya `ms-appx-web` bir mutlak URI oluşturmak için düzeni.  
  
 Aşağıdaki örnekte nasıl ayarlanacağını gösterir [kaynak](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) özelliği için bir [WebView](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) denetim ve [kaynak](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) özelliği için bir [görüntü](http://msdn.microsoft.com/library/windows/apps/br242752.aspx) denetimi XAML ve kod sayfaları adlı bir klasörde yer alan kaynakları için kullanma.  
  
 [!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
 Bu düzenleri hakkında daha fazla bilgi için bkz: [URI şemaları](http://msdn.microsoft.com/library/windows/apps/jj655406.aspx) Windows geliştirme Merkezi'ndeki.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
