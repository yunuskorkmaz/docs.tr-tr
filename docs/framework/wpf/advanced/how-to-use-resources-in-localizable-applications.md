---
title: 'Nasıl yapılır: Yerelleştirilebilir Uygulamalarda Kaynak Kullanımı'
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: ad257e7703bcee8f71da78ad5928d7999365c38f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376172"
---
# <a name="how-to-use-resources-in-localizable-applications"></a>Nasıl yapılır: Yerelleştirilebilir Uygulamalarda Kaynak Kullanımı
Yerelleştirme anlamına gelir uyum sağlamak bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] farklı kültürler için. Başlık gibi metin bunun için açıklamalı alt yazılar, liste kutusu öğeleri ve diğerleri çevrilecek sahip. Çeviri kolaylaştırmak için kaynak dosyalarına çevrilmesi için öğeleri toplanır. Bkz: [bir uygulamayı yerelleştirme](how-to-localize-an-application.md) yerelleştirme için bir kaynak dosyasının nasıl oluşturulacağı hakkında bilgi için. Yapmak için bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerelleştirilebilir geliştiricilerin gereken bir kaynağı derlemeye tüm yerelleştirilebilir kaynakları oluşturmak bir uygulama. Kaynak derlemesi farklı dilde yerelleştirilmiş olan ve kaynak yönetimi arka plan kod kullanır [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] yüklenemedi. İçin gerekli dosyaları birini bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir proje dosyası (.proj) uygulamasıdır. Uygulamanızda kullandığınız tüm kaynakları, proje dosyasında eklenmelidir. Aşağıdaki kod örneği bunu gösterir.  
  
## <a name="example"></a>Örnek  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 Bir kaynak kullanmak için örneği <xref:System.Resources.ResourceManager> ve kullanmak istediğiniz kaynak yükleyin. Bunun nasıl yapılacağı gösterilmektedir.  
  
 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
