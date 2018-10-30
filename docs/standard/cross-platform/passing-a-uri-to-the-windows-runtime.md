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
ms.openlocfilehash: c5ce0d4ac2b95dc4d51e785e3a00026f56c13d2c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220713"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>URI'yı Windows Çalışma Zamanı'na Geçirme
Windows çalışma zamanı yöntemleri, yalnızca mutlak URI kabul eder. Göreli bir URI geçirirseniz bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] yöntemi, bir <xref:System.ArgumentException> özel durumu oluşturulur. İşte nedenleri: kullandığınızda [!INCLUDE[wrt](../../../includes/wrt-md.md)] .NET Framework kodunda <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıfı olarak görünür <xref:System.Uri?displayProperty=nameWithType> IntelliSense içinde. <xref:System.Uri?displayProperty=nameWithType> Sınıfı göreli URI'ler sağlar ancak <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıfı yok. Bu da içinde ortaya çıkarttığınız yöntemler için doğru [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşenleri. Bileşeniniz URI alan bir yöntem sunarsa, kodunuzdaki imzası içerir <xref:System.Uri?displayProperty=nameWithType>. Ancak bileşeninizin kullanıcıları için imza içerir <xref:Windows.Foundation.Uri?displayProperty=nameWithType>. Bileşeninize iletilen bir URI mutlak URI olmalıdır.  
  
Bu konuda, bir mutlak URI tespit etme ve bir uygulama paketinde bir kaynağa başvuran nasıl oluşturulduğu gösterilmektedir.  
  
## <a name="detecting-and-using-an-absolute-uri"></a>Algılama ve mutlak URI kullanma  
Kullanım <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> geçirmeden önce bir URI mutlak olduğundan emin olmak için özellik [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Bu özellik kullanılarak durumunun yakalanmasından ve işlenmesinden verimlidir <xref:System.ArgumentException> özel durum.  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>Uygulama paketinde bir kaynak için bir mutlak URI kullanma  
Uygulama paketinizi içeren bir kaynak için URI belirtmek istiyorsanız, kullanabileceğiniz `ms-appx` veya `ms-appx-web` düzenini mutlak URI oluşturmak için.  
  
Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> özelliği için bir <xref:Windows.UI.Xaml.Controls.WebView> denetimi ve <xref:Windows.UI.Xaml.Controls.Image.Source%2A> özelliği için bir <xref:Windows.UI.Xaml.Controls.Image> hem XAML hem kod kullanarak sayfaları adlı bir klasörde bulunan kaynaklara denetimi.  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
Bu şemalar hakkında daha fazla bilgi için bkz. [URI düzenleri](/windows/uwp/app-resources/uri-schemes) Windows geliştirme Merkezi'nde.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
