---
title: 示例业务方案和无服务器应用的用例
description: 通过访问范围的示例从映像处理到移动后端和 ETL 管道了解亲自动手实践的无服务器体验。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: c38d1c6c4e04f3fa38946c97af5d94758b3ed6f7
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "49369662"
---
# <a name="serverless-business-scenarios-and-use-cases"></a><span data-ttu-id="c39b2-103">无服务器业务方案和用例</span><span class="sxs-lookup"><span data-stu-id="c39b2-103">Serverless business scenarios and use cases</span></span>

<span data-ttu-id="c39b2-104">有许多用例和方案的无服务器应用程序。</span><span class="sxs-lookup"><span data-stu-id="c39b2-104">There are many use cases and scenarios for serverless applications.</span></span> <span data-ttu-id="c39b2-105">本章包括示例，用于演示不同的方案。</span><span class="sxs-lookup"><span data-stu-id="c39b2-105">This chapter includes samples that illustrate the different scenarios.</span></span> <span data-ttu-id="c39b2-106">方案包括指向相关的文档和公共源代码存储库。</span><span class="sxs-lookup"><span data-stu-id="c39b2-106">The scenarios include links to related documentation and public source code repositories.</span></span> <span data-ttu-id="c39b2-107">这一章中的示例，可以开始您自己构建和实现无服务器解决方案。</span><span class="sxs-lookup"><span data-stu-id="c39b2-107">The samples in this chapter enable you to get started on your own building and implementing serverless solutions.</span></span>

## <a name="analyze-and-archive-images"></a><span data-ttu-id="c39b2-108">分析和归档图像</span><span class="sxs-lookup"><span data-stu-id="c39b2-108">Analyze and archive images</span></span>

<span data-ttu-id="c39b2-109">此示例演示无服务器事件 （事件网格）、 工作流 （逻辑应用） 和代码 (Azure Functions)。</span><span class="sxs-lookup"><span data-stu-id="c39b2-109">This sample demonstrates serverless events (Event Grid), workflows (Logic App), and code (Azure Functions).</span></span> <span data-ttu-id="c39b2-110">它还演示如何将与另一个资源，图像分析此事例认知服务中进行集成。</span><span class="sxs-lookup"><span data-stu-id="c39b2-110">It also shows how to integrate with another resource, in this case Cognitive Services for image analysis.</span></span>

<span data-ttu-id="c39b2-111">控制台应用程序，可传递一个链接到的 URL 在 web 上找到。</span><span class="sxs-lookup"><span data-stu-id="c39b2-111">A console application allows you to pass a link to a URL on the web.</span></span> <span data-ttu-id="c39b2-112">应用程序发布 URL 作为事件网格消息。</span><span class="sxs-lookup"><span data-stu-id="c39b2-112">The app publishes the URL as an event grid message.</span></span> <span data-ttu-id="c39b2-113">并行情况下，无服务器函数应用和逻辑应用订阅该消息。</span><span class="sxs-lookup"><span data-stu-id="c39b2-113">In parallel, a serverless function app and a logic app subscribe to the message.</span></span> <span data-ttu-id="c39b2-114">无服务器函数应用序列化到 blob 存储的映像。</span><span class="sxs-lookup"><span data-stu-id="c39b2-114">The serverless function app serializes the image to blob storage.</span></span> <span data-ttu-id="c39b2-115">它还存储在 Azure 表存储中的信息。</span><span class="sxs-lookup"><span data-stu-id="c39b2-115">It also stores information in Azure Table Storage.</span></span> <span data-ttu-id="c39b2-116">元数据将存储原始图像 URL 和 blob 映像的名称。</span><span class="sxs-lookup"><span data-stu-id="c39b2-116">The metadata stores the original image URL and the name of the blob image.</span></span> <span data-ttu-id="c39b2-117">逻辑应用使用自定义视觉 API 分析图像并创建计算机生成的标题进行交互。</span><span class="sxs-lookup"><span data-stu-id="c39b2-117">The logic app interacts with the Custom Vision API to analyze the image and create a machine-generated caption.</span></span> <span data-ttu-id="c39b2-118">标题存储在元数据表中。</span><span class="sxs-lookup"><span data-stu-id="c39b2-118">The caption is stored in the metadata table.</span></span>

![分析和归档映像体系结构](./media/image-processing-example.png)

<span data-ttu-id="c39b2-120">单独的单页应用程序 (SPA) 调用来获取的图像和元数据列表的无服务器函数。</span><span class="sxs-lookup"><span data-stu-id="c39b2-120">A separate single page application (SPA) calls a serverless function to get a list of images and metadata.</span></span> <span data-ttu-id="c39b2-121">对于每个映像，它将调用从存档中提供的图像数据的另一个函数。</span><span class="sxs-lookup"><span data-stu-id="c39b2-121">For each image, it calls another function that delivers the image data from the archive.</span></span> <span data-ttu-id="c39b2-122">最终结果是具有自动字幕的库。</span><span class="sxs-lookup"><span data-stu-id="c39b2-122">The final result is a gallery with automatic captions.</span></span>

![自动化的图像库](./media/automated-image-gallery.png)

<span data-ttu-id="c39b2-124">此处提供的完整存储库和生成逻辑应用的说明：[事件网格粘附](https://github.com/JeremyLikness/Event-Grid-Glue)。</span><span class="sxs-lookup"><span data-stu-id="c39b2-124">The full repository and instructions to build the logic app are available here: [Event grid glue](https://github.com/JeremyLikness/Event-Grid-Glue).</span></span>

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a><span data-ttu-id="c39b2-125">跨平台移动客户端使用 Xamarin.Forms 和函数</span><span class="sxs-lookup"><span data-stu-id="c39b2-125">Cross-platform mobile client using Xamarin.Forms and functions</span></span>

<span data-ttu-id="c39b2-126">了解如何在 Azure Web 门户中或在 Visual Studio 中实现一个简单的无服务器 Azure 函数。</span><span class="sxs-lookup"><span data-stu-id="c39b2-126">See how to implement a simple serverless Azure Function in the Azure Web Portal or in Visual Studio.</span></span> <span data-ttu-id="c39b2-127">生成 Android、 iOS 和 Windows 运行的 Xamarin.Forms 具有的客户端。</span><span class="sxs-lookup"><span data-stu-id="c39b2-127">Build a client with Xamarin.Forms that runs on Android, iOS, and Windows.</span></span> <span data-ttu-id="c39b2-128">应用程序然后优化为服务器和使用无服务器的后端的移动客户端之间的通信中使用 JavaScript 对象表示法 (JSON)。</span><span class="sxs-lookup"><span data-stu-id="c39b2-128">The application is then refined to use JavaScript Object Notation (JSON) as a communication medium between the server and the mobile clients with a serverless back end.</span></span>

<span data-ttu-id="c39b2-129">有关详细信息，请参阅[使用 Xamarin.Forms 客户端和实施一个简单的 Azure 函数](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)</span><span class="sxs-lookup"><span data-stu-id="c39b2-129">For more information, see [Implementing a simple Azure Function with a Xamarin.Forms client](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)</span></span>

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a><span data-ttu-id="c39b2-130">生成无服务器的图像识别与照片马赛克</span><span class="sxs-lookup"><span data-stu-id="c39b2-130">Generate a photo mosaic with serverless image recognition</span></span>

<span data-ttu-id="c39b2-131">该示例使用 Azure Functions 和 Microsoft 认知服务自定义影像服务从输入图像生成照片马赛克。</span><span class="sxs-lookup"><span data-stu-id="c39b2-131">The sample uses Azure Functions and Microsoft Cognitive Services Custom Vision Service to generate a photo mosaic from an input image.</span></span> <span data-ttu-id="c39b2-132">训练模型来识别图像。</span><span class="sxs-lookup"><span data-stu-id="c39b2-132">The model is trained to recognize images.</span></span> <span data-ttu-id="c39b2-133">上传图像时，它可以识别图像，并使用必应搜索。</span><span class="sxs-lookup"><span data-stu-id="c39b2-133">When an image is uploaded, it recognizes the image and searches with Bing.</span></span> <span data-ttu-id="c39b2-134">原始图像是重新组合使用搜索结果。</span><span class="sxs-lookup"><span data-stu-id="c39b2-134">The original image is recomposed using the search results.</span></span>

![奥兰多关注照片和马赛克](./media/orlando-eye-both.png)

<span data-ttu-id="c39b2-136">例如，你可以训练奥兰多的地标，例如奥兰多关注与您的模型。</span><span class="sxs-lookup"><span data-stu-id="c39b2-136">For example, you can train your model with Orlando landmarks, such as the Orlando Eye.</span></span> <span data-ttu-id="c39b2-137">自定义影像将识别的奥兰多只眼，映像并为该函数将创建照片马赛克组成必应图像搜索结果"奥兰多眼。"</span><span class="sxs-lookup"><span data-stu-id="c39b2-137">Custom Vision will recognize an image of the Orlando Eye, and the function will create a photo mosaic composed of Bing image search results for "Orlando Eye."</span></span>

<span data-ttu-id="c39b2-138">有关详细信息，请参阅[Azure Functions 照片马赛克生成器](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)。</span><span class="sxs-lookup"><span data-stu-id="c39b2-138">For more information, see [Azure Functions photo mosaic generator](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/).</span></span>

## <a name="migrate-an-existing-application-to-the-cloud"></a><span data-ttu-id="c39b2-139">迁移到云的现有应用程序</span><span class="sxs-lookup"><span data-stu-id="c39b2-139">Migrate an existing application to the cloud</span></span>

<span data-ttu-id="c39b2-140">如前面几章中所述，很常见欣然接受要在应用程序在本地托管的 N 层体系结构。</span><span class="sxs-lookup"><span data-stu-id="c39b2-140">As discussed in previous chapters, it's common to embrace an N-Tier architecture to host your application on-premises.</span></span> <span data-ttu-id="c39b2-141">尽管迁移资源"按原样"使用虚拟机到云至少风险的路径，许多公司选择使用机会来重构其应用程序。</span><span class="sxs-lookup"><span data-stu-id="c39b2-141">Although migrating resources "as is" using virtual machines is the least risky path to the cloud, many companies choose to use the opportunity to refactor their applications.</span></span> <span data-ttu-id="c39b2-142">幸运的是，重构不一定要"要么"的工作。</span><span class="sxs-lookup"><span data-stu-id="c39b2-142">Fortunately, refactoring doesn't have to be an "all-or-nothing" effort.</span></span> <span data-ttu-id="c39b2-143">事实上，它是可以迁移您的应用程序然后段落组件将替换为云本机函数。</span><span class="sxs-lookup"><span data-stu-id="c39b2-143">In fact, it's possible to migrate your app then piecemeal replace components with cloud native counterparts.</span></span>

<span data-ttu-id="c39b2-144">应用程序使用 Azure Functions 代理功能使重构到无服务器终结点的终结点从旧的本地代码。</span><span class="sxs-lookup"><span data-stu-id="c39b2-144">The application uses the proxies feature of Azure Functions to enable refactoring an endpoint from legacy on-premises code to a serverless endpoint.</span></span>

![迁移体系结构](./media/migration-architecture.png)

<span data-ttu-id="c39b2-146">代理提供了更新以将单个请求重新路由，因为它们将被移动到无服务器函数的单个 API 终结点。</span><span class="sxs-lookup"><span data-stu-id="c39b2-146">The proxy provides a single API endpoint that is updated to reroute individual requests as they're moved into serverless functions.</span></span>

<span data-ttu-id="c39b2-147">您可以查看视频，介绍了如何通过在整个迁移：[提升和使用无服务器 Azure functions 的 shift](https://channel9.msdn.com/Events/Connect/2017/E102)。</span><span class="sxs-lookup"><span data-stu-id="c39b2-147">You can view a video that walks through the entire migration: [Lift and shift with serverless Azure functions](https://channel9.msdn.com/Events/Connect/2017/E102).</span></span> <span data-ttu-id="c39b2-148">访问示例代码：[使你自己的应用](https://github.com/JeremyLikness/bring-own-app-connect-17)。</span><span class="sxs-lookup"><span data-stu-id="c39b2-148">Access the sample code: [Bring your own app](https://github.com/JeremyLikness/bring-own-app-connect-17).</span></span>

## <a name="parse-a-csv-file-and-insert-into-a-database"></a><span data-ttu-id="c39b2-149">分析 CSV 文件并将插入到数据库</span><span class="sxs-lookup"><span data-stu-id="c39b2-149">Parse a CSV file and insert into a database</span></span>

<span data-ttu-id="c39b2-150">提取、 转换和加载 (ETL) 是集成不同的系统的常见业务函数。</span><span class="sxs-lookup"><span data-stu-id="c39b2-150">Extract, Transform, and Load (ETL) is a common business function that integrates different systems.</span></span> <span data-ttu-id="c39b2-151">设置专用的 FTP 服务器，然后部署计划的作业来分析文件并将它们转换用于商业用途，通常涉及到传统的方法。</span><span class="sxs-lookup"><span data-stu-id="c39b2-151">Traditional approaches often involve setting up dedicated FTP servers then deploying scheduled jobs to parse files and translate them for business use.</span></span> <span data-ttu-id="c39b2-152">无服务器体系结构使作业更容易，因为该文件上传时为可以激发触发器。</span><span class="sxs-lookup"><span data-stu-id="c39b2-152">Serverless architecture makes the job easier because a trigger can fire when the file is uploaded.</span></span> <span data-ttu-id="c39b2-153">Azure 函数处理任务，如通过专注于特定的问题小代码段其理想组合 ETL。</span><span class="sxs-lookup"><span data-stu-id="c39b2-153">Azure Functions tackles tasks like ETL through its ideal composition of small pieces of code that focus on a specific problem.</span></span>

![ETL 体系结构](./media/csvimport.png)

<span data-ttu-id="c39b2-155">源代码和动手实验，请参阅[CSV 导入实验室](https://github.com/JeremyLikness/azure-fn-file-process-hol)。</span><span class="sxs-lookup"><span data-stu-id="c39b2-155">For source code and a hands-on lab, see [CSV import lab](https://github.com/JeremyLikness/azure-fn-file-process-hol).</span></span>

## <a name="shorten-links-and-track-metrics"></a><span data-ttu-id="c39b2-156">请缩短链接，然后跟踪指标</span><span class="sxs-lookup"><span data-stu-id="c39b2-156">Shorten links and track metrics</span></span>

<span data-ttu-id="c39b2-157">最初帮助简单地说编码 Url 的链接缩短工具 twitter 帖子，以适应 140 个字符限制。</span><span class="sxs-lookup"><span data-stu-id="c39b2-157">Link shortening tools originally helped encode URLs in short twitter posts to accommodate the 140 character limit.</span></span> <span data-ttu-id="c39b2-158">它们已发展起来，包含几种用法，通常以跟踪各单击操作进行分析。</span><span class="sxs-lookup"><span data-stu-id="c39b2-158">They've grown to encompass several uses, most commonly to track click-throughs for analytics.</span></span> <span data-ttu-id="c39b2-159">链接 shortener 示例方案是完全无服务器应用程序的管理链接和报告指标。</span><span class="sxs-lookup"><span data-stu-id="c39b2-159">The link shortener scenario is an entirely serverless application that manages links and reports metrics.</span></span>

<span data-ttu-id="c39b2-160">Azure 函数用于为单页应用程序 (SPA)，您可以将长 URL 粘贴并生成短 Url 提供服务。</span><span class="sxs-lookup"><span data-stu-id="c39b2-160">Azure Functions is used to serve a Single Page Application (SPA) that allows you to paste the long URL and generate short URLs.</span></span> <span data-ttu-id="c39b2-161">Url 标记来跟踪活动 （主题） 和媒体 （如链接发布到的社交网络） 等内容。</span><span class="sxs-lookup"><span data-stu-id="c39b2-161">The URLs are tagged to track things like campaigns (topics) and mediums (such as social networks that the links are posted to).</span></span> <span data-ttu-id="c39b2-162">短代码作为键，作为值的长 url 存储在 Azure 表存储中。</span><span class="sxs-lookup"><span data-stu-id="c39b2-162">The short code is stored in Azure Table Storage as the key, with the long URL as the value.</span></span> <span data-ttu-id="c39b2-163">单击的短链接时，另一个函数查找长 URL、 发送重定向，并将有关事件的信息放在队列上。</span><span class="sxs-lookup"><span data-stu-id="c39b2-163">When you click on the short link, another function looks up the long URL, sends a redirect, and places information about the event on a queue.</span></span> <span data-ttu-id="c39b2-164">另一个 Azure 函数处理队列，并将放入 Azure Cosmos DB 的信息。</span><span class="sxs-lookup"><span data-stu-id="c39b2-164">Another Azure Function processes the queue and places the information into Azure Cosmos DB.</span></span>

![链接 shortener 示例体系结构](./media/link-shortener-architecture.png)

<span data-ttu-id="c39b2-166">然后，可以创建 Power BI 仪表板来收集有关收集的数据的见解。</span><span class="sxs-lookup"><span data-stu-id="c39b2-166">You can then create a Power BI dashboard to gather insights about the data collected.</span></span> <span data-ttu-id="c39b2-167">在后端，Application Insights 提供了重要的指标。</span><span class="sxs-lookup"><span data-stu-id="c39b2-167">On the back end, Application Insights provides important metrics.</span></span> <span data-ttu-id="c39b2-168">遥测数据包括需要多长时间的平均用户重定向和访问 Azure 表存储所需的时间长度。</span><span class="sxs-lookup"><span data-stu-id="c39b2-168">Telemetry includes how long it takes for the average user to redirect and how long it takes to access Azure Table Storage.</span></span>

![Power BI 示例](./media/power-bi-example.png)

<span data-ttu-id="c39b2-170">此处提供了说明的完整链接 shortener 示例存储库：[的无服务器的 URL shortener 示例](https://github.com/jeremylikness/serverless-url-shortener)。</span><span class="sxs-lookup"><span data-stu-id="c39b2-170">The full link shortener repository with instructions is available here: [Serverless URL shortener](https://github.com/jeremylikness/serverless-url-shortener).</span></span> <span data-ttu-id="c39b2-171">你可以阅读此处的简化版本：[无服务器的.NET 应用程序，以分钟为单位的 Azure 存储](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/)。</span><span class="sxs-lookup"><span data-stu-id="c39b2-171">You can read about a simplified version here: [Azure Storage for serverless .NET apps in minutes](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/).</span></span>

## <a name="verify-device-connectivity-using-a-ping"></a><span data-ttu-id="c39b2-172">验证使用 ping 的设备连接</span><span class="sxs-lookup"><span data-stu-id="c39b2-172">Verify device connectivity using a ping</span></span>

<span data-ttu-id="c39b2-173">此示例包含的 Azure IoT 中心和 Azure 函数。</span><span class="sxs-lookup"><span data-stu-id="c39b2-173">The sample consists of an Azure IoT Hub and an Azure Function.</span></span> <span data-ttu-id="c39b2-174">IoT 中心中的新消息触发 Azure 函数。</span><span class="sxs-lookup"><span data-stu-id="c39b2-174">A new message on the IoT Hub triggers the Azure Function.</span></span> <span data-ttu-id="c39b2-175">无服务器代码返回到发送它的设备发送同一消息内容。</span><span class="sxs-lookup"><span data-stu-id="c39b2-175">The serverless code sends the same message content back to the device that sent it.</span></span> <span data-ttu-id="c39b2-176">项目都有解决方案所需的所有代码和部署配置。</span><span class="sxs-lookup"><span data-stu-id="c39b2-176">The project has all the code and deployment configuration needed for the solution.</span></span>

<span data-ttu-id="c39b2-177">有关详细信息，请参阅[Azure IoT 中心 ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)。</span><span class="sxs-lookup"><span data-stu-id="c39b2-177">For more information, see [Azure IoT Hub ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/).</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="c39b2-178">推荐的资源</span><span class="sxs-lookup"><span data-stu-id="c39b2-178">Recommended resources</span></span>

* [<span data-ttu-id="c39b2-179">Azure Functions 照片马赛克生成器</span><span class="sxs-lookup"><span data-stu-id="c39b2-179">Azure Functions photo mosaic generator</span></span>](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)
* [<span data-ttu-id="c39b2-180">Azure IoT 中心 ping</span><span class="sxs-lookup"><span data-stu-id="c39b2-180">Azure IoT Hub ping</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)
* [<span data-ttu-id="c39b2-181">以分钟为单位的无服务器.NET 应用程序的 azure 存储</span><span class="sxs-lookup"><span data-stu-id="c39b2-181">Azure Storage for serverless .NET apps in minutes</span></span>](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/)
* [<span data-ttu-id="c39b2-182">将你自己的应用</span><span class="sxs-lookup"><span data-stu-id="c39b2-182">Bring your own app</span></span>](https://github.com/JeremyLikness/bring-own-app-connect-17)
* [<span data-ttu-id="c39b2-183">CSV 导入实验室</span><span class="sxs-lookup"><span data-stu-id="c39b2-183">CSV import lab</span></span>](https://github.com/JeremyLikness/azure-fn-file-process-hol)
* [<span data-ttu-id="c39b2-184">事件网格粘附</span><span class="sxs-lookup"><span data-stu-id="c39b2-184">Event grid glue</span></span>](https://github.com/JeremyLikness/Event-Grid-Glue)
* [<span data-ttu-id="c39b2-185">使用 Xamarin.Forms 客户端和实施一个简单的 Azure 函数</span><span class="sxs-lookup"><span data-stu-id="c39b2-185">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)
* [<span data-ttu-id="c39b2-186">提升和转移无服务器 Azure functions</span><span class="sxs-lookup"><span data-stu-id="c39b2-186">Lift and shift with serverless Azure functions</span></span>](https://channel9.msdn.com/Events/Connect/2017/E102)
* [<span data-ttu-id="c39b2-187">无服务器的 URL shortener 示例</span><span class="sxs-lookup"><span data-stu-id="c39b2-187">Serverless URL shortener</span></span>](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
<span data-ttu-id="c39b2-188">[上一页](orchestration-patterns.md)
[下一页](serverless-conclusion.md)</span><span class="sxs-lookup"><span data-stu-id="c39b2-188">[Previous](orchestration-patterns.md)
[Next](serverless-conclusion.md)</span></span>