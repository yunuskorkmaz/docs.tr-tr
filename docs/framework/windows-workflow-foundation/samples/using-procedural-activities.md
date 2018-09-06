---
title: Yordam etkinlikleri kullanma
ms.date: 03/30/2017
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
ms.openlocfilehash: bd83f1a0fa9f3af7c22cee73fbc4f984a9ebf53c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43804784"
---
# <a name="using-procedural-activities"></a><span data-ttu-id="92f48-102">Yordam etkinlikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="92f48-102">Using Procedural Activities</span></span>
<span data-ttu-id="92f48-103">Örnek kullanır <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, ve <xref:System.Activities.Statements.WriteLine> bir tahmin uygulamak için etkinlikleri oyun.</span><span class="sxs-lookup"><span data-stu-id="92f48-103">The sample uses the <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, and <xref:System.Activities.Statements.WriteLine> activities to implement a guessing game.</span></span> <span data-ttu-id="92f48-104">Tahmin eden oyun rastgele bir sayı seçer ve bu sayıyı tahmin oyuncusu içeriyor.</span><span class="sxs-lookup"><span data-stu-id="92f48-104">The guessing game selects a random number and the player has to guess that number.</span></span> <span data-ttu-id="92f48-105">Oyuncu bir yanlış tahmin gönderdiğinde, iş akışını tahmin daha yüksek veya daha düşük bir ipucu sağlar.</span><span class="sxs-lookup"><span data-stu-id="92f48-105">When the player submits an incorrect guess, the workflow provides a hint whether to guess higher or lower.</span></span> <span data-ttu-id="92f48-106">Yürütücü numarası 7'den az girişimlerinde tahminler, kullanıcıya özel Tebrikler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="92f48-106">If the player guesses the number in less than 7 attempts, a special congratulations is displayed to the user.</span></span>  
  
## <a name="custom-activities-in-this-sample"></a><span data-ttu-id="92f48-107">Bu örnekte özel etkinlikler</span><span class="sxs-lookup"><span data-stu-id="92f48-107">Custom Activities in this Sample</span></span>  
  
### <a name="readline"></a><span data-ttu-id="92f48-108">ReadLine</span><span class="sxs-lookup"><span data-stu-id="92f48-108">ReadLine</span></span>  
 <span data-ttu-id="92f48-109">Bir metin satırı konsolundan okur.</span><span class="sxs-lookup"><span data-stu-id="92f48-109">Reads a line of text from the console.</span></span> <span data-ttu-id="92f48-110">Bu etkinlik türetildiği <xref:System.Activities.NativeActivity> sınıfı ve bir satırı okumak, konsol uygulaması tarafından sürdürüldü bir yer işareti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="92f48-110">This activity derives from the <xref:System.Activities.NativeActivity> class and creates a bookmark that is resumed by the console application when a line is read.</span></span>  
  
### <a name="promptint"></a><span data-ttu-id="92f48-111">PromptInt</span><span class="sxs-lookup"><span data-stu-id="92f48-111">PromptInt</span></span>  
 <span data-ttu-id="92f48-112">Kullanıcıdan bir sayı yazın ve ardından konsol penceresinden okur.</span><span class="sxs-lookup"><span data-stu-id="92f48-112">Prompts the user to type in a number and then reads it from a console window.</span></span> <span data-ttu-id="92f48-113">Etkinlik türetildiği <xref:System.Activities.Activity%601> ve kullandığı <xref:System.Activities.Statements.WriteLine> ve `ReadLine` etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="92f48-113">The activity derives from <xref:System.Activities.Activity%601> and uses the <xref:System.Activities.Statements.WriteLine> and `ReadLine` activities.</span></span>  
  
##### <a name="to-use-this-sample"></a><span data-ttu-id="92f48-114">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="92f48-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="92f48-115">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], GuessingGame.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="92f48-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the GuessingGame.sln solution file.</span></span>  
  
2.  <span data-ttu-id="92f48-116">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="92f48-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="92f48-117">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="92f48-117">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="92f48-118">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="92f48-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="92f48-119">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="92f48-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="92f48-120">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="92f48-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="92f48-121">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="92f48-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`