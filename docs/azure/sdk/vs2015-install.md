---
title: Visual Studio 2015 için Azure araçları
description: Visual Studio 2015'teki Azure .NET kitaplıklarını kullanmaya başlamak için araçları alın.
ms.date: 10/19/2017
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: a29709d56f2debe04d49ee4eafdc27acd4ca480f
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071929"
---
# <a name="azure-tools-for-visual-studio-2015"></a>Visual Studio 2015 için Azure araçları

**Visual Studio 2015 için Azure SDK** ve **Service Fabric SDK ve Visual Studio 2015 Araçları** için yüklemenin en hızlı ve en kolay yolu Web Platform [Installer'ı](https://www.microsoft.com/web/downloads/platform.aspx)kullanmaktır. Microsoft Web Platform Installer, Visual Studio 2015 için Azure araçları da dahil olmak üzere Microsoft Web Platformu'nun bazı bileşenlerini indirme, yükleme ve güncelleştirmeyi kolaylaştıran ücretsiz bir araçtır. Bu [SDK'lar, Azure İndirmeler sayfasından](https://azure.microsoft.com/downloads/)tek tek bileşenler olarak indirilebilir ve yüklenebilir.

## <a name="using-the-web-platform-installer"></a>Web Platform Yükleyicisini Kullanma

1. İndirin ve bu [Web Platformu Installer bootstrapper](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015)çalıştırın.

2. Bootstrapper Web Platform Installer'ı (gerekirse) yükler ve visual **studio 2015 için Azure SDK'nın** en son sürümlerini ve **Hizmet Kumaşı SDK ve Visual Studio için Araçlar 2015** öğelerini öğelerinize otomatik olarak *yüklenecek öğelere* koyar. **Yükle'yi**tıklatın.

    ![Web Platformu Yükleyicisi](../media/sdk/vs2015-install/webpi.png)

3. Sonraki ekranda Kabul **Ediyorum'u**tıklatın. Web PI, seçtiğiniz bileşenleri indirmeye ve yüklemeye başlar.

4. Yükleme tamamlandıktan sonra bir onay ekranı görüntülenir. **Son**'a tıklayın. Artık Web Platformu Yükleyici'yi kapatabilirsiniz.

## <a name="verifying-the-installation"></a>Yüklemenin doğrulanması

1. Visual Studio 2015'te **Araçlar** menüsüne tıklayın ve **ardından Uzantılar ve Güncellemeler'i tıklatın...**.

2. Görüntülenen listede **Microsoft Azure Uygulama Hizmet Araçları, Microsoft** **Azure Depolama Bağlantılı Hizmet**ve Hizmet Kumaş **Araçları**gibi çeşitli Azure araçları bulunur.

    ![Uzantılar ve güncellemeler](../media/sdk/vs2015-install/ext-tools.png)
