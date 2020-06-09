---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: d64be95f71f840e08ede63e1c1f14ee08e52ce97
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592482"
---
# <a name="configurationcodegenerator"></a><span data-ttu-id="25693-102">ConfigurationCodeGenerator</span><span class="sxs-lookup"><span data-stu-id="25693-102">ConfigurationCodeGenerator</span></span>
<span data-ttu-id="25693-103">ConfigurationCodeGenerator, özel kanal uygulamalarınızı yapılandırma sistemine sunmak için kullanabileceğiniz bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="25693-103">The ConfigurationCodeGenerator is a tool that you can use to expose your custom channel implementations to the configuration system.</span></span> <span data-ttu-id="25693-104">Bu, özel kanalınızın kullanıcılarının `NetTcpBinding` , veya kullanarak özel bir bağlama gibi sistem tarafından sağlanmış bir bağlamayı yapılandırdıkları gibi bir. config dosyası kullanarak kanalınızı yapılandırmasına olanak sağlar `TcpTransportBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="25693-104">This allows users of your custom channel to configure your channel by using a .config file just as they would configure a system-provided binding such as `NetTcpBinding` or a custom binding using the `TcpTransportBindingElement`.</span></span>  
  
 <span data-ttu-id="25693-105">Bir özel kanal yazdığınızda ve bunu yeni bir veya kullanarak programlama modelinde kullanıma sundığınızda, bir `BindingElement` `Binding` `BindingElement` `Binding` . config dosyası kullanarak veya yapılandırılabilir hale getirmek için bir sınıf kümesi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="25693-105">When you write a custom channel and expose it to the programming model by using a new `BindingElement` or `Binding`, you must create a set of classes to make the `BindingElement` or `Binding` configurable using a .config file.</span></span> <span data-ttu-id="25693-106">Bu sınıfları oluşturmak ve müşterinizin deneyimini geliştirmek için ConfigurationCodeGenerator aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25693-106">You can use the ConfigurationCodeGenerator tool to generate these classes and enhance your customer's experience.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="25693-107">Aracı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="25693-107">To build the tool</span></span>  
  
1. <span data-ttu-id="25693-108">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="25693-108">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="25693-109">Çözümün oluşturulması bir dosya oluşturur: ConfigurationCodeGenerator. exe.</span><span class="sxs-lookup"><span data-stu-id="25693-109">Building the solution generates one file: ConfigurationCodeGenerator.exe.</span></span> <span data-ttu-id="25693-110">SampleRun. cmd dosyası, [taşıma: UDP](transport-udp.md) örneği için sınıfları oluşturmak üzere bu aracın nasıl kullanılacağını gösteren örnek bir komut satırına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="25693-110">The file SampleRun.cmd has a sample command line that shows how to use this tool to generate the classes for the [Transport: UDP](transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="25693-111">Aracı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="25693-111">To run the tool</span></span>  
  
1. <span data-ttu-id="25693-112">Komut isteminde, hem özel bir `BindingElement` tür hem de özel bir tür varsa aşağıdakini yazın `Binding` :</span><span class="sxs-lookup"><span data-stu-id="25693-112">At the command prompt type the following if you have both a custom `BindingElement` type and a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     <span data-ttu-id="25693-113">Ya da yalnızca özel bir tür varsa şunları yazın `BindingElement` :</span><span class="sxs-lookup"><span data-stu-id="25693-113">Or type the following if you have only a custom `BindingElement` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="25693-114">Ya da yalnızca özel bir tür varsa şunları yazın `Binding` :</span><span class="sxs-lookup"><span data-stu-id="25693-114">Or type the following if you have only a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="25693-115">Komut için üç. cs dosyası `BindingElement` (/be: Option belirttiyseniz), standart için beş. cs dosyası `Binding` (/SB: Option belirttiyseniz) ve bir. xml dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="25693-115">The command generates three .cs files for the `BindingElement` (if you specified the /be: option), five .cs files for the standard `Binding` (if you specified the /sb: option), and a .xml file.</span></span>  
  
    1. <span data-ttu-id="25693-116">/İn seçeneğini kullandıysanız,. cs dosyalarından biri `BindingElementExtensionSection` bağlama öğesi için öğesini uygular.</span><span class="sxs-lookup"><span data-stu-id="25693-116">If you used the /be option, one of the .cs files implements the `BindingElementExtensionSection` for your binding element.</span></span> <span data-ttu-id="25693-117">Bu kod `BindingElement` , diğer özel Bağlamalarınızın bağlama öğesini kullanabilmesi için yapılandırma sistemine bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="25693-117">This code exposes your `BindingElement` to the configuration system, so that other custom bindings can use your binding element.</span></span> <span data-ttu-id="25693-118">Diğer dosyalarda varsayılanlar ve sabitleri temsil eden sınıflar vardır.</span><span class="sxs-lookup"><span data-stu-id="25693-118">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="25693-119">Dosyalar, `//TODO` varsayılan değerleri güncelleştirmenizi hatırlatmak için yorumlardır.</span><span class="sxs-lookup"><span data-stu-id="25693-119">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
    2. <span data-ttu-id="25693-120">/SB seçeneğini belirlediyseniz,. cs dosyalarından ikisi `StandardBindingElement` sırasıyla bir ve `StandardBindingCollectionElement` , yapılandırma sistemine standart bağlamayı sunan bir ve uygular.</span><span class="sxs-lookup"><span data-stu-id="25693-120">If you specified the /sb option, two of the .cs files implement a `StandardBindingElement` and a `StandardBindingCollectionElement` respectively, which exposes your standard binding to the configuration system.</span></span> <span data-ttu-id="25693-121">Diğer dosyalarda varsayılanlar ve sabitleri temsil eden sınıflar vardır.</span><span class="sxs-lookup"><span data-stu-id="25693-121">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="25693-122">Dosyalar, `//TODO` varsayılan değerleri güncelleştirmenizi hatırlatmak için yorumlardır.</span><span class="sxs-lookup"><span data-stu-id="25693-122">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
         <span data-ttu-id="25693-123">/SB: seçeneğini belirlediyseniz CodeToAddTo. cs ' nin \<*YourStdBinding*> Standart bağlamayı uygulayan sınıfa el ile eklemeniz gereken kodu vardır.</span><span class="sxs-lookup"><span data-stu-id="25693-123">If you specified the /sb: option the CodeToAddTo\<*YourStdBinding*>.cs has code that you must manually add into the class that implements your standard binding.</span></span>  
  
     <span data-ttu-id="25693-124">SampleConfig. xml dosyası, önceki 1 veya 2. adımda tanımlanan işleyicileri kaydeden yapılandırma dosyasına eklemeniz gereken yapılandırma kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="25693-124">The SampleConfig.xml file contains the configuration code that you must add to the configuration file that registers the handlers defined in the previous step 1 or 2.</span></span>  
