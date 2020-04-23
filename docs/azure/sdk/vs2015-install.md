---
title: Visual Studio için Azure Araçları 2015
description: Visual Studio 2015 ' den Azure .NET kitaplıklarını kullanmaya başlamak için Araçları alın.
ms.date: 10/19/2017
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: a29709d56f2debe04d49ee4eafdc27acd4ca480f
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071929"
---
# <a name="azure-tools-for-visual-studio-2015"></a>Visual Studio için Azure Araçları 2015

**Visual studio 2015 Için Azure SDK 'sını** ve **Visual studio 2015 için Service Fabric SDK ve araçları** yüklemenin en hızlı ve en kolay yolu [Web Platformu Yükleyicisi](https://www.microsoft.com/web/downloads/platform.aspx)'ni kullanmaktır. Microsoft Web Platformu Yükleyicisi, Visual Studio 2015 için Azure araçları dahil olmak üzere Microsoft Web Platformu bileşenlerini indirmeyi, yüklemeyi ve güncellemeyi kolaylaştıran ücretsiz bir araçtır. Bu SDK 'lar Ayrıca [Azure İndirmeleri sayfasından](https://azure.microsoft.com/downloads/)ayrı bileşenler olarak indirilip yüklenebilir.

## <a name="using-the-web-platform-installer"></a>Web Platformu Yükleyicisi 'ni kullanma

1. Bu [Web platformu yükleyici Bootstrapper](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015)'nı indirip çalıştırın.

2. Önyükleyici, Web Platformu Yükleyicisi 'ni yükler (gerekirse) ve **Visual studio 2015 Için Azure SDK** 'nın en son sürümlerini ve visual Studio 2015 IÇIN **Service Fabric SDK ve araçlar** 'ı otomatik olarak yerleştirir. *Items to be installed* **Install**'a tıklayın.

    ![Web Platformu Yükleyicisi](../media/sdk/vs2015-install/webpi.png)

3. Sonraki ekranda **kabul ediyorum**' a tıklayın. Web PI seçtiğiniz bileşenleri indirmeye ve yüklemeye başlayacak.

4. Yükleme tamamlandıktan sonra, bir onay ekranı görüntülenir. **Son**'a tıklayın. Artık Web Platformu Yükleyicisi 'ni kapatabilirsiniz.

## <a name="verifying-the-installation"></a>Yüklemenin doğrulanması

1. Visual Studio 2015 ' de **Araçlar** menüsüne ve ardından **Uzantılar ve Güncelleştirmeler ' e tıklayın...**

2. Görüntülenmiş listede **Microsoft Azure App Service araçları**, **Microsoft Azure depolama bağlı hizmet**ve **Service Fabric araçları**gibi çeşitli Azure araçları yer alacak.

    ![Uzantılar ve güncelleştirmeler](../media/sdk/vs2015-install/ext-tools.png)
